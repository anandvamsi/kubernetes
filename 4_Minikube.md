# Minikube
If you want to try something in the local environement without creating clusters or in case where you
dont have any resources memory/cpu ..etc

Minikube is single node K8s cluster where master and worker node process resides in the single node.
docker container pre-installed.
Minikube is a lightweight Kubernetes (K8) installation, which can create a Virtual Machine (VM) on your local machine or in a cloud instance, which deploys a simple cluster containing only one nod

minikube create a vbox on your laptop, kubectl is the client to connect the minikube.

Minikube installation prerequiste:
- 2 CPUs or more
- 2GB of free memory
- 20GB of free disk space
- Internet connection

# Installation of Minikube in Amazon linux

step1: Install docker 
```code
yum install docker
systemctl enable docker
systemctl start docker
```

step1.a Install kubectl 
```code
curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.26.2/2023-03-17/bin/linux/amd64/kubectl
 cp kubectl /usr/local/bin
```

step 2: install the minikube
```code
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

step 3: Minikube Intialization
```code
**/usr/local/bin/minikube  start --force**
😄  minikube v1.32.0 on Amazon 2 (xen/amd64)
❗  minikube skips various validations when --force is supplied; this may lead to unexpected behavior
✨  Using the docker driver based on existing profile
🛑  The "docker" driver should not be used with root privileges. If you wish to continue as root, use --force.
💡  If you are running minikube within a VM, consider using --driver=none:
📘    https://minikube.sigs.k8s.io/docs/reference/drivers/none/
💡  Tip: To remove this root owned cluster, run: sudo minikube delete
👍  Starting control plane node minikube in cluster minikube
🚜  Pulling base image ...
🤷  docker "minikube" container is missing, will recreate.
🔥  Creating docker container (CPUs=2, Memory=2200MB) ...
🐳  Preparing Kubernetes v1.28.3 on Docker 24.0.7 ...
    ▪ Generating certificates and keys ...
    ▪ Booting up control plane ...
    ▪ Configuring RBAC rules ...
🔗  Configuring bridge CNI (Container Networking Interface) ...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🔎  Verifying Kubernetes components...
🌟  Enabled addons: storage-provisioner, default-storageclass
💡  kubectl not found. If you need it, try: 'minikube kubectl -- get pods -A'
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
```
Verifying the Minikube status.
```code

# minikube status
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```

Verifying the pods
```
kubectl get pods -A
NAMESPACE     NAME                               READY   STATUS    RESTARTS      AGE
kube-system   coredns-5dd5756b68-lrc5z           1/1     Running   0             30m
kube-system   etcd-minikube                      1/1     Running   0             30m
kube-system   kube-apiserver-minikube            1/1     Running   0             30m
kube-system   kube-controller-manager-minikube   1/1     Running   0             30m
kube-system   kube-proxy-pmp9c                   1/1     Running   0             30m
kube-system   kube-scheduler-minikube            1/1     Running   0             30m
kube-system   storage-provisioner                1/1     Running   1 (30m ago)   30m
```
