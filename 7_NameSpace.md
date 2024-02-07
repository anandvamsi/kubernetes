# Namespace in kubernetes
  Organise resources in namespaces.
  virtual cluster in K8s cluster.

# Life without Namespaces and Benefits of namespaces.
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
kubectl create namespace <namespacename>
kubectl apply -f db.yaml --namespace=mongons
Another method is to include the namespace under the metadata.
```


    
