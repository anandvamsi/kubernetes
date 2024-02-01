# Kubernetes Components.
- Node:- VM/physical node.
- Pod:-
    - Smallest unit of K8s
    - Abstract over container
    - Usually 1 application/pod, But we can run multiple container in one Pod.
    - Each Pod will have 1 IP
    - Pods are emphernal means when pods die and recreated, it will get NEW IP address.
      
- Service:
    Permanent IP address assigned to Pod, even if the Pod dies the IP address of the service retains(so we dont have to change the IP each time)
- Ingress:-
