### Kubernetes CLI commands

## To deploy application with deployment.

```bash
kubectl run web1 --image=nginx --replica=2 myprod1 -n myprod2
```
Notes:-
This will create pods,deployment and replicaset any changes in the deployment will create a new version in the replicaset

## To delete all the resources in specifc namespace
```bash
kubectl delete all --all  -n myprod`
```
## To delete all the pods to spefic namespace
```bash
kubectl delete pod -n myprod
```
Note if pods are deleting ,it wont create because there is no scheduler/deployment if this has used using the generator while creating pods.

## To show the details  of the pod 
```bash
kubectl get pods -o wide  -n myprod
```

## sort-pods by time 
```bash
kubectl get pod -A --sort-by={metadata.creationTimestamp}
```

# How to add IAM role as the cluster admin; Below command has to executed Elevated users
```eksctl create iamidentitymapping --cluster <clustername> --region=us-west-2 --arn arn:aws:iam::XXXXXXX:role/UsersGroupAdmin --group system:masters --username admin ```
