# sort-pods by time 
kubectl get pod -A --sort-by={metadata.creationTimestamp}

# How to add IAM role as the cluster admin; Below command has to executed Elevated users
```eksctl create iamidentitymapping --cluster <clustername> --region=us-west-2 --arn arn:aws:iam::XXXXXXX:role/UsersGroupAdmin --group system:masters --username admin ```
