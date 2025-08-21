# Annotations
Annotations are like sticky notes you attach to Kubernetes objects (like Pods, Deployments, Services, etc.) to store non-identifying metadata. Unlike labels (which are used for selecting and grouping objects), 
annotations are used to store arbitrary information that tools or humans might need.

Think of it this way:
Labels = used by Kubernetes itself to organize and manage resources.
Annotations = used by external tools or humans to add extra info that Kubernetes doesn’t act on directly.

Example.
Let’s say you’re deploying a Pod and you want your monitoring tool (like Prometheus or Datadog) to know how to scrape metrics from it.

```bash
apiVersion: v1
kind: Pod
metadata:
  name: my-app
  annotations:
   prometheus.io/scrape: "true"
    prometheus.io/port: "8080"
spec:
  containers:
  - name: my-app-container
    image: my-app-image
    ports:
    - containerPort: 8080
```
prometheus.io/scrape: "true" tells Prometheus to scrape metrics from this Pod.
prometheus.io/port: "8080" tells it which port to use.
Prometheus reads these annotations and configures itself accordingly. Kubernetes itself doesn’t care about these annotations—they’re just metadata.

Annotations in Kubernetes are mostly user-defined, meaning you can create your own keys and values to store any metadata you want. 
However, some tools and platforms use specific annotation keys that are expected to follow a certain format or naming convention
```bash
annotations:
  deployed.by: "anand.vamsi"
  purpose: "testing new feature"
  team: "infra"
```
These are completely custom and used by you or your internal tools.

Some tools expect annotations with specific keys. These are not "reserved" by Kubernetes itself, but they are standardized by the tool. Examples:

```bash
prometheus.io/scrape: "true"
prometheus.io/port: "8080"
nginx.ingress.kubernetes.io/rewrite-target: /
argocd.argoproj.io/instance: my-app
```
These annotations are recognized by the respective tools, and they expect specific formats or values.
