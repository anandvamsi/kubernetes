# Kubernetes

## What is Kuberntes
Kubernetes is a container orchestration tool developed by google. 

## What is kubernetes and what problems does the kubernetes solve.

- High available  or no down time
- Scalibility or high performance
- Disaster recovery - backup and restore(deployments)


## Kubernetes Architecture
Master nodes and Worker  nodes.

Master node: 
- Have the process that requrired to maintain and manage entire kubernetes cluster.

   -  ```API server```:- Entry point to K8 cluter(UI,API,CLI )
   - ```controller Manager``` :- keeps track of whats ** happening in the cluster**, if anything is repaired,restarted
   - ``` scheduler``` :- Keeps track of pods replacement should be intelligent enought in which worker node the new pod has to replaced(load average, availability).
   - ```etcd``` :- keeps the configuration details in the form of KV(Key value pair), recover the cluster state.
   -``` Virtual Network``` :- Enable the communication between Master Node and Worker Node

Note:- If we loose master node,we cannot access any of the resources inside the  worker nodes.
In the production cluster, we will have two copies of the master node.




Worker Node:
On the worker nodes you are applications are running.


## Kubernetes Basic Concepts.
```pod``` ::- Smallest 
Ratio is 1 pod: 1 container, some times we need multiple containers pods(databased,message broker)
Each pod will have an IP address, That how pod communicates.
