# Kubectl commands


## Deployment 
Deployments are a higher-level abstraction built on top of the Kubernetes Pods and ReplicaSets.
A Deployment is a management tool for controlling the behavior of pods. By default, Kubernetes runs one instance for each Pod you create. However, by defining a Deployment object, you can specify that Kubernetes should run multiple instances of the pod. 
Behind the scenes, the Deployment object creates ReplicaSets to run the required instances of the po

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
