# Namespace in kubernetes
  Organise resources in namespaces.
  virtual cluster in K8s cluster.

## Life without Namespaces and Benefits of namespaces.
- All the objects fall under single default namespace :- unorganized
- Imagine more than 1 team working on same K8s cluster, if they have resources/object names this wil create a conflicts
- smaller companies/Projects will have same cluster  if they want stagging,Dev resources in same cluster this will create  problems.
- we can restrict users to specific namespaces(create isolation).
- we can limit the CPU,RAM,Storage per NS:- Resouce quota.
- Each Namespace should uses its own name config maps and secrets , they cannot use other namespaces config-maps/secrets.
- Only service can share the share across the NS.
- Volumes and Nodes are two componets which cannot be the part of the namespaces.
  

## Default namespaces in minikube.
  - Kube system
  - kube public
  - kube node release
  - default::- All the resouces created without the namespaces placed in this namespace


## Namespace commands
```bash

[root@ip-10-80-224-32 ec2-user]# kubectl get ns
NAME              STATUS   AGE
default           Active   2d2h
kube-node-lease   Active   2d2h
kube-public       Active   2d2h
kube-system       Active   2d2h

kubectl create ns mongo
namespace/mongo created

kubectl apply -f db.yaml --namespace=mongons
Another method is to include the namespace under the metadata.
```

# KubeNS
  kubens is the command that will show the current namespace

    
