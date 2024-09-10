Pre-requieste package to install 
-----------------------------------
step1:: Install AWSCLI

step2::Install kubectl
Install aws version 2.2
Install kubectl 1.26
curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.26.2/2023-03-17/bin/linux/amd64/kubectl
mv /usr/local/bin

## Install EKSCTL
```bash
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
mv /tmp/eksctl /usr/local
```


## Create cluster with eksctl with existing VPC
```bash
eksctl create cluster \
  --name N3 \
  --region us-west-2 \
  --version 1.28 \
  --vpc-private-subnets subnet-047c8caae88d24be6,subnet-0bc434d8c9f250263 \
  --nodegroup-name ng-1 \
  --node-type t2.micro \
  --nodes 2 \
  --nodes-min 1 \
  --nodes-max 2
```


## eksctl delete the cluster
```bash
 eksctl delete cluster --name N2 --region us-west-2
2024-09-10 10:15:29 [ℹ]  deleting EKS cluster "N2"
2024-09-10 10:15:30 [ℹ]  will drain 0 unmanaged nodegroup(s) in cluster "N2"
2024-09-10 10:15:30 [ℹ]  starting parallel draining, max in-flight of 1
2024-09-10 10:15:30 [✖]  failed to acquire semaphore while waiting for all routines to finish: context canceled
2024-09-10 10:15:34 [ℹ]  deleted 0 Fargate profile(s)
2024-09-10 10:15:35 [ℹ]  cleaning up AWS load balancers created by Kubernetes objects of Kind Service or Ingress
2024-09-10 10:15:37 [ℹ]
2 sequential tasks: { delete nodegroup "ng-1", delete cluster control plane "N2" [async]
}
2024-09-10 10:15:38 [ℹ]  will delete stack "eksctl-N2-nodegroup-ng-1"
2024-09-10 10:15:38 [ℹ]  waiting for stack "eksctl-N2-nodegroup-ng-1" to get deleted
2024-09-10 10:15:38 [ℹ]  waiting for CloudFormation stack "eksctl-N2-nodegroup-ng-1"
2024-09-10 10:16:08 [ℹ]  waiting for CloudFormation stack "eksctl-N2-nodegroup-ng-1"
2024-09-10 10:16:08 [ℹ]  will delete stack "eksctl-N2-cluster"
2024-09-10 10:16:08 [✔]  all cluster resources were deleted
```
