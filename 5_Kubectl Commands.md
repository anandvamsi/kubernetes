# Kubectl commands


## Deployment 
Deployments are a higher-level abstraction built on top of the Kubernetes Pods and ReplicaSets.
A Deployment is a management tool for controlling the behavior of pods. By default, Kubernetes runs one instance for each Pod you create. However, by defining a Deployment object, you can specify that Kubernetes should run multiple instances of the pod. 
Behind the scenes, the Deployment object creates ReplicaSets to run the required instances of the pod

Note: The Deployment object eliminates the need for administrators to manually run pods on Kubernetes nodes
if we remove the deployment this will eventually remove the respective replicaset and pods.

## Replicaset

A ReplicaSet is a Kubernetes object that runs multiple instances of a pod and ensures a certain number of pods is running at all times.
When a pod fails, the ReplicaSet immediately starts a new instance of the pod. At any given time, if the number of running instances does not match the specified number, it scales up and creates another instance of the pod with the same label. If there are extra pods, the ReplicaSet scales down by removing them.

By contrast, a Deployment is a higher-level concept that manages ReplicaSets and provides declarative updates to pods along with many other features. The Kubernetes documentation recommends that users do not directly work with ReplicaSets, instead using Deployments.

## TO create a nginx deployment
```bash
kubectl create deployment mongodel --image=mongo
```
## To view the deployment, replicaset, pods
```
kubectl  get deployments
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
mongod             1/1     1            1           19m
nginx-deployment   1/1     1            1           30m

kubectl  get replicaset
NAME                          DESIRED   CURRENT   READY   AGE
mongod-5c65944cb9             1         1         1       20m
nginx-deployment-6644f659f    1         1         1       25m
nginx-deployment-6d6565499c   0         0         0       30m


kubectl  get pods
NAME                               READY   STATUS    RESTARTS   AGE
mongod-5c65944cb9-9vhjt            1/1     Running   0          20m
nginx-deployment-6644f659f-b69dw   1/1     Running   0          25m
```

## Running the deployment with multiple replicas.
```
kubectl create deployment nginx2 --replicas=2 --image=nginx
```

## To edit the deployment
```
kubectl edit deployment <deployment-name>
>> the image version
```
This will update the existing deployment of the application by creating a new replicaset and pods


## Debugging the pods
```code
Kubect logs <podname>
kubectl describe pod <podname>
kubectl exec  -it <podname> -- bin/bash
```





