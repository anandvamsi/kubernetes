# Blue Green Deployment
- Blue-Green Deployment is a release strategy where you run two environments (Blue and Green) at the same time:
  - Blue = current version (stable, serving users)
  - Green = new version (candidate release, deployed in parallel)
- When you’re confident Green is good, you switch traffic from Blue → Green.
- if something goes wrong, you can quickly rollback by routing traffic back to Blue.
- In Kubernetes, this usually means two Deployments (blue and green) and one Service that switches between them.


## How it Works in Kubernetes
### Step 1 – Deploy Blue (v1)
Blue deployment runs pods of version v1 of your app.
Service routes all traffic to Blue.

### Step 2 – Deploy Green (v2)
Deploy a new set of pods (Green) with version v2.
They exist alongside Blue pods but don’t receive production traffic yet.

### Step 3 – Switch Traffic
Update the Service’s label selector from app=blue → app=green.
Now traffic goes to Green (v2).

### Step 4 – Rollback (if needed)
If v2 has issues, just point the Service back to Blue.

## BlueGreen Deployment Manifes
### Blue
```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-blue
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
      version: blue
  template:
    metadata:
      labels:
        app: myapp
        version: blue
    spec:
      containers:
      - name: myapp
        image: myapp:v1
```
### Green
```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-green
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
      version: green
  template:
    metadata:
      labels:
        app: myapp
        version: green
    spec:
      containers:
      - name: myapp
        image: myapp:v2
```

### Service manifest
```bash
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:
  selector:
    app: myapp
    version: blue   # 🔄 change this to 'green' to switch traffic
  ports:
  - port: 80
    targetPort: 80
```


### Use Cases of Blue-Green Deployment

- Zero downtime upgrades (switch is instant).
- Quick rollback (just repoint service).
- Testing in production — Green runs in the same cluster, so you can test before releasing.
- Safe releases for critical apps where downtime or bugs are unacceptable.
