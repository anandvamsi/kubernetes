# DaemonSet
- A DaemonSet = “one pod per node” workload, best for running cluster-wide agents like logging, monitoring, networking, or security tools.
- A DaemonSet is a Kubernetes workload object that ensures a copy of a Pod runs on every (or selected) node in the cluster.

- If a new node joins the cluster → Kubernetes automatically schedules the DaemonSet Pod on it.
- If a node is removed → the DaemonSet Pod on that node is also removed.
- You can also restrict it to certain nodes using labels + nodeSelector / affinity.

```bash
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: node-logger
spec:
  selector:
    matchLabels:
      app: logger
  template:
    metadata:
      labels:
        app: logger
    spec:
      containers:
      - name: logger
        image: fluentd:latest
```
## Here are typical usecase of a Daemonset
DaemonSets are ideal for workloads that need to run on all (or specific) nodes for system-level or monitoring tasks:

### Log Collection
Deploy logging agents (e.g., Fluentd, Filebeat) on all nodes to collect logs and ship them to Elasticsearch, CloudWatch, or Splunk.

### Monitoring / Metrics
Run monitoring agents (e.g., Prometheus Node Exporter, Datadog Agent, New Relic) on every node to collect CPU, memory, disk, and network metrics.

### Networking
Deploy CNI plugins (like Calico, Flannel, Cilium) which need to run on each node to manage pod networking.

### Security Agents
Run security tools (e.g., Falco, antivirus scanners, intrusion detection agents) on every node.

### Storage
Deploy CSI (Container Storage Interface) drivers or storage daemons that must exist on each node to handle volumes.

### Node-Specific Services
Example: A caching or proxy service that must run on each node for local access
