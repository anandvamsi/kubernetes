### Kubernetes CLI commands

### To deploy application with deployment.

```bash
kubectl run web1 --image=nginx --replica=2 myprod1 -n myprod2
```
Notes:-
This will create pods,deployment and replicaset any changes in the deployment will create a new version in the replicaset

- Any changes in the deployment will create new replicat set version which affects respecive pods 



### To expose any application to outside:- This will create service
```bash
kubectl expose <deployment name> --port 8080 --target-port=8080 -n myprod1
```
### To create a route for the service using oc :- Route is Openshift resources.
```bash
oc expose <service name> -n myprod`
```
- Note:- syntax of the hostname created ```<appname>:<namepsace>:<sudomain>```
- Here is an example web1-myprod1.apps.ocp4.example.com
- Using the service IP, we can access from inside the cluster
- Using the expose URL, we can access the cluster from outside the cluster using hostname url

### To need help in creating parameters
```bash
kubectl create ingress --help | more
```

### OC commands
```bash
oc get route -n myprod1
oc get rs  -n myprod
oc get svc -n myprod
oc get route -n myprod
```
### To get help from 
```bash
oc explain pod
oc explain deployment
oc explain rs
```




### To delete all the resources in specifc namespace
```bash
kubectl delete all --all  -n myprod`
```
### To delete all the pods to spefic namespace
```bash
kubectl delete pod -n myprod
```
Note if pods are deleting ,it wont create because there is no scheduler/deployment if this has used using the generator while creating pods.

### To show the details  of the pod 
```bash
kubectl get pods -o wide  -n myprod
```

### sort-pods by time 
```bash
kubectl get pod -A --sort-by={metadata.creationTimestamp}
```

### How to add IAM role as the cluster admin; Below command has to executed Elevated users
```eksctl create iamidentitymapping --cluster <clustername> --region=us-west-2 --arn arn:aws:iam::XXXXXXX:role/UsersGroupAdmin --group system:masters --username admin ```
