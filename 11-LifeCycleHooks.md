# LifeCycle Hooks

Lifecycle hooks let you execute commands during the container lifecycle. postStart runs right after the container starts, useful for initialization like registering with a monitoring service. preStop runs before termination, useful for cleanup like deregistering or closing connections gracefully. 
They complement init containers, which run before any main containers start.

##
postStart is non-blocking for the Pod creation, but if it fails, the container restarts.
preStop is useful to clean up resources or gracefully notify services before termination.
Hooks run inside the same container, unlike initContainers which run in separate containers

```bash
apiVersion: v1
kind: Pod
metadata:
  name: nginx-lifecycle
spec:
  containers:
  - name: nginx
    image: nginx:1.25
    ports:
      - containerPort: 80
    lifecycle:
      postStart:
        exec:
          command: ["/bin/sh", "-c", "echo Registering container with monitoring service"]
      preStop:
        exec:
          command: ["/bin/sh", "-c", "echo Deregistering container from monitoring service; sleep 5"]
```
### postStart
```bash
Runs immediately after the container starts.
Example command registers the container with a monitoring system.
```

### preStop
```bash
Runs before the container terminates.
Example command deregisters the container and sleeps 5 seconds to allow graceful shutdown.
```
