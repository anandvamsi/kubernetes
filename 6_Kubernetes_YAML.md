# YAML File Explained.

YAML is human friendly data serialization standard for all the programming languages.
- syntax is strict indentation 
- Use YAML Online editor to check the syntax and indentation
- 
1. Metadata
     A. Need to mention what kind we are going to create, Deployment,Service.
   
2. ```Specification```:

3. ```Status```: In this segment K8s compares what is the actual difference between actuals and desired
if there is difference K8s make it meets the desired as per the configration.

Note: ETCD holds the status information regarding the cluster.
   

