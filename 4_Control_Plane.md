# Control Plane
The control plane in Kubernetes is the set of components responsible for managing the overall state of the cluster.

The control plane consist of:

```Kube-apiserver```: This is the API server that exposes the Kubernetes API. I
It is the front-end for the Kubernetes control plane. 

- Main entry point to the control plane (acts like a front-end).
- Accepts and processes RESTful API calls (from kubectl, other components, etc.).
- Validates requests, and updates the cluster state in etcd.
- Is stateless – can be scaled horizontally (multiple instances for HA).


```etcd```: This is a distributed key-value store that stores the cluster's configuration data,
representing the overall state of the cluster. The etcd database is used as the single source of truth for the entire cluster.
etcd is considered as the cluster brain 
- what resources are available
- Did the cluster state changed.
- Application deployment state.
- Only the application data is not stored in ETCD.
-  Even if a pods dies, etcd redirects to create a new Pod in the same worker node.
Note:- Kubernetes wont take the backup of etcd, it is advised to take the backup of etcd and store in remote-storage.

```Kube-scheduler```: The scheduler is responsible for determining where to run newly created Pods based on factors such as resource requirements, node affinity, 
and anti-affinity rules. It assigns Pods to suitable worker nodes.

- Node affinity ::- means "I prefer or require my pod to run on nodes that have specific labels"
Affinity: Run GPU workloads only on nodes with GPU (node-type=gpu)

- Node Anti-Affinity ::- I prefer or require not to run my pod on nodes with certain labels.
  
```Controller Manager```:
The Controller Manager in Kubernetes is like the brain behind the scenes that keeps everything running as expected. It's responsible for monitoring the cluster state and taking action to make sure it matches the desired state defined in the specs (like Deployments, ReplicaSets, etc.).
```bash
Controller | What it Does
Node Controller | Watches node health, handles unresponsive nodes.
Replication Controller | Ensures the correct number of pod replicas are running.
Deployment Controller | Manages rolling updates and rollbacks.
Namespace Controller | Cleans up resources in deleted namespaces.
Service Account Controller | Creates default service accounts and tokens.
Job/TTL Controller | Handles cleanup of completed jobs and TTL-based cleanup.
Endpoint Controller | Manages the endpoint objects tied to services.
```


Master nodes requires less resources(CPU|RAM|Storage) compared to worker nodes.
