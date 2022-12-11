# Introduction to Containers / K8s / OpenShift

The labs in this repo were tested in a Fedora 36 system with the following hardware and software versions:

Hardware:

 - 4 vCPUs
 - 4 GiB RAM
 - 30 GB HD

Software:
    
  - Podman v4.3.1
  - Podman Compose v1.0.3
  - Kubectl v1.25.5
  - Kind v0.11.1

## Preparing the system for the labs

1. Connect to the Fedora 35 system
2. Install Podman and podman-compose

    ~~~sh
    sudo dnf install -y podman podman-compose
    ~~~
3. Install Kubectl 

    ~~~sh
    sudo curl -L https://dl.k8s.io/release/v1.25.5/bin/linux/amd64/kubectl -o /usr/local/bin/kubectl
    sudo chmod +x /usr/local/bin/kubectl
    ~~~
4. Install Kind

    ~~~sh
    sudo curl -L https://github.com/kubernetes-sigs/kind/releases/download/v0.17.0/kind-linux-amd64 -o /usr/local/bin/kind
    sudo chmod +x /usr/local/bin/kind
    ~~~
