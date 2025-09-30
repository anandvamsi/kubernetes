# Node Selector.
- In Kubernetes, a NodeSelector is the simplest way to tell the scheduler which nodes a Pod is allowed to run on.
- It works by matching labels on nodes with constraints on Pods.
- You add a nodeSelector field in your Pod/Deployment spec, and the scheduler will place the Pod only on nodes that have the matching label.

```bash
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
  - name: nginx
    image: nginx
  nodeSelector:
    disktype: ssd
```
## Notes
- If a node has the label disktype=ssd, this Pod can run there.
- Otherwise, the scheduler won’t place in it

### Important to Note 
- With nodeSelector, if labels don’t match any node → Pod stays in Pending forever until

## Use cases of Node selector

### Workload Placement Based on Hardware
- Example: Place I/O heavy workloads on nodes with disktype=ssd.
- Example: ML/AI workloads only on GPU nodes (accelerator=nvidia).

### Isolation of Environments
- Example: Run production workloads only on nodes labeled env=prod.
- Helps keep dev/test workloads separate from production nodes.

### Cost Optimization
- Example: Direct batch jobs to cheaper spot instances (lifecycle=spot).
- Keep critical workloads on on-demand instances (lifecycle=on-demand).

### Compliance and Security
- Example: Place workloads handling sensitive data only on nodes in specific AZs or with encryption enabled.

