# Introduction to Containers / K8s / OpenShift

The labs in this repo were tested in a Fedora 43 system with the following hardware and software versions:

Hardware:

- 4 vCPUs
- 4 GiB RAM
- 40 GB HD

Software:

- Podman
- Podman Compose
- Kubectl v1.34.0
- Kind v0.30.0

## Preparing the system for the labs

1. Create the script that prepares the VM

    ~~~sh
    cat << EOF > prepare_env.sh
    #!/bin/bash
    sudo dnf5 group install workstation-product-environment -y
    sudo systemctl set-default graphical.target
    sudo useradd student -G wheel
    echo "student:student" | chpasswd
    sudo dnf install -y podman podman-compose virtualbox-guest-additions
    sudo curl -L https://dl.k8s.io/release/v1.34.0/bin/linux/amd64/kubectl -o /usr/local/bin/kubectl
    sudo chmod +x /usr/local/bin/kubectl
    sudo curl -L https://github.com/kubernetes-sigs/kind/releases/download/v0.30.0/kind-linux-amd64 -o /usr/local/bin/kind
    sudo chmod +x /usr/local/bin/kind
    sudo -iu student podman pull docker.io/library/hello-world:latest
    sudo -iu student podman pull docker.io/library/httpd:2.4
    sudo -iu student podman pull docker.io/library/ubuntu:22.04
    sudo -iu student podman pull docker.io/golang:1.23
    sudo -iu student podman pull quay.io/mavazque/pacman:latest
    sudo -iu student podman pull docker.io/library/mongo:5.0
    sudo podman pull docker.io/kindest/node:v1.34.0@sha256:7416a61b42b1662ca6ca89f02028ac133a309a2a30ba309614e8ec94d976dc5a
    sudo podman pull quay.io/mavazque/pacman:latest
    sudo podman pull docker.io/library/mongo:5.0
    sudo reboot
    EOF
    ~~~

2. Create the VM

    ~~~sh
    kcli create vm -i fedora43 -P numcpus=4 -P memory=4096 -P name=rha-2026 -P disks=[40] -P scripts=[prepare_env.sh]
    ~~~
