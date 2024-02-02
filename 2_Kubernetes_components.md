# Kubernetes Components.
- ```Node```:- VM/physical node.
- ```Pod```:-
    - Smallest unit of K8s
    - A layer of abstract over container
    - Usually 1 application/pod, But we can run multiple container in one Pod.
    - Each Pod will have 1 IP
    - Pods are emphernal means when pods die and recreated, it will get NEW IP address.
      
- ```Service```:
    Permanent IP address assigned to Pod, even if the Pod dies the IP address of the service retains(so we dont have to change the IP each time).
    service will also act as a load balancer which means it can distribute the traffic to the underlying pods.
  
- ```Ingress```:-
      In production, sending request to URL is not preferred  compared to hostname, Ingress solves this problem
       All the request first hits the Ingress and Ingress forwads the traffic to Service
- ```Config-maps```:
      Usually database related configration stores in the container,But Imagine a case where DB config needs to changed, In that case we need to change container config and rebuild it which is tedious task.
       ```Config-maps``` stores the external configration of the application like the DB_URL and other servies.
       Note: Its not recommended to store the username,password of the application

- ```Secrets```: Used to store secreat data encoded in base64 (passwords,certificates), pods should read the data from config-maps and secrets.

- ```Volumes```: attaches a storage volume to pod, it can be local storage or a remote outside of K8s cluster, so even if the pod is restated , still the data presits.
  Note :- K8s does't manages the data presistance```, we have the setup the replication

- ```Deployment```: Determintes how many pods replicates we would like to run, Deployment is another layer of abstration on Pods.
  we mostly work with deployments not directly over pods.
   It provides a declarative way to define and manage the desired state of your application, ensuring that the specified number of instances (pods) are running and healthy.
  Deployments which are suitable for stateless applications that can be easily replicated and scaled horizontally
  
- ```Statefulset``` : This componets is suited for database(mysql,mongodb,elasticsearch), All the Database should be created by the statefulset not via deployments.
  Deploying application using Statefulset is bit challanging, that is the reason why DBs are often hosted outside of K8s clusters.
  StatefulSets are designed for applications that require stable network identities, stable storage, and ordered deployment and scaling.
  
