# What is containerD in NutShell.
containerd is an industry-standard container runtime that acts as the engine Kubernetes uses to actually run containers on each node. It's a daemon for Linux and Windows that handles the complete container lifecycle:``` pulling and storing images, executing containers, supervising them, and attaching storage and networking```

## Flow of containerd
- You submit a Pod to the Kubernetes API.
- The scheduler assigns it to a node.
- That node's kubelet sends a CRI request to containerd.
- containerd pulls the image, prepares the filesystem, and launches a lower-level runtime (like runc) that actually starts the container process

### OneLiner
```In short: Kubernetes orchestrates, containerd executes.```

## What is CTR
ctr is the command-line client that ships with containerd for interacting directly with the containerd daemo
```bash
ctr images pull docker.io/library/nginx:latest
ctr run docker.io/library/nginx:latest mynginx
ctr containers list
```

## What is Nerdctl
nerdctl is a Docker-compatible command-line tool for containerd. 
```It gives you the familiar docker-style commands (run, build, ps, images, compose) while talking directly to containerd instead of the Docker daemo```

```bash
nerdctl run -d --name web -p 8080:80 nginx
nerdctl ps
nerdctl images
nerdctl build -t myapp:latest .
nerdctl compose up -d
```
## what is Crictl
- critcl provides a CLI for CRI comptaible container run times like rkt,containerd
- Installed sepertely
- Used to inspects debug container runtimes
- works across different run times
