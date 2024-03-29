# Control Plane
The control plane in Kubernetes is the set of components responsible for managing the overall state of the cluster.

The control plane consist of:

```Kube-apiserver```: This is the API server that exposes the Kubernetes API. I
It is the front-end for the Kubernetes control plane. 

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

```Controller Manager```: The controller manager runs controller processes that regulate the state of the system. 
Controllers are responsible for handling tasks such as node and pod lifecycle management, maintaining the desired state.
-   ```Node Controller```: Responsible for monitoring the nodes in the cluster and responding to changes in node availability or health.
-   ```Replication Controller```: Ensures the specified number of replicas for a pod are running and maintains the desired state.


Master nodes requires less resources(CPU|RAM|Storage) compared to worker nodes.
