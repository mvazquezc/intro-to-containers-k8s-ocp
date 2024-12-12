# Introduction to Containers / K8s / OpenShift

The labs in this repo were tested in a Fedora 41 system with the following hardware and software versions:

Hardware:

- 4 vCPUs
- 4 GiB RAM
- 30 GB HD

Software:

- Podman
- Podman Compose
- Kubectl v1.31.2
- Kind v0.25.0

## Preparing the system for the labs

1. Connect to the Fedora 41 system
2. Install Required software

    ~~~sh
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo > /dev/null
    sudo dnf install -y podman podman-compose code openjdk
    ~~~

3. Install Kubectl 

    ~~~sh
    sudo curl -L https://dl.k8s.io/release/v1.31.2/bin/linux/amd64/kubectl -o /usr/local/bin/kubectl
    sudo chmod +x /usr/local/bin/kubectl
    ~~~

4. Install Kind

    ~~~sh
    sudo curl -L https://github.com/kubernetes-sigs/kind/releases/download/v0.25.0/kind-linux-amd64 -o /usr/local/bin/kind
    sudo chmod +x /usr/local/bin/kind
    ~~~

5. Cache Images

    ~~~sh
    podman pull docker.io/library/hello-world:latest
    podman pull docker.io/library/httpd:2.4
    podman pull docker.io/library/ubuntu:22.04
    podman pull docker.io/golang:1.23
    podman pull quay.io/ifont/pacman-nodejs-app:latest
    podman pull docker.io/library/mongo:5.0
    sudo podman pull docker.io/kindest/node:v1.31.2@sha256:18fbefc20a7113353c7b75b5c869d7145a6abd6269154825872dc59c1329912e
    sudo podman pull quay.io/ifont/pacman-nodejs-app:latest
    sudo podman pull docker.io/library/mongo:5.0
    ~~~