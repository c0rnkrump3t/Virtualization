# Containers:
---

## What is a Container?
A container is a isolated group of  processes that run on a single host and acts as a complete application. Containers do not have an OS or kernel.
![[Pasted image 20220601233830.png]]

## How do Containers work?
Containers are based on functions that the kernel uses to isolate applications. Though the applications are isolated they belong to a similar Linux environment. A Linux Container Daemon (LXD) is used to run containers on the same system. LXCs are container based virtualization technologies that function at the OS level and can help automate mass container management. Each container is based on the file system. Containers are scalable and can be managed by orchestration systems like Apache Mesos and Google Kubernetes.

## What is Docker?
Docker is similar to virtualization, but it’s a software that packages applications in containers. It is useful because it simplifiees application deployment as data can be transported and installed easily. Programs and their dependancies are stored through images that can be run on almost all Operating Systems.

### Installing Docker on Fedora
1. Use this command to download package information from all configured sources

```bash
sudo yum update -y
```

2.  To install  dnf-plugins-core
```bash
 sudo dnf install dnf-plugins-core
```

3.  To add the docker repo
```bash
sudo dnf config-manager --add-repo [https://download.docker.com/linux/fedora/docker-ce.repo](https://download.docker.com/linux/fedora/docker-ce.repo)
```

4.  To install docker engine
```bash
sudo dnf install docker-ce docker-ce-cli containerd.io
```

5.  To start docker
```bash
sudo systemctl start docker
```

6.  To test if docker installed correctly
```bash
sudo docker run hello-world
``` 

7.  OPTIONAL: To make docker start at startup
```bash
sudo systemctl enable docker
```

## What is the Docker Engine?

The Docker Engine is used to build and contain applications. It provides an interface between host resources and running containers.

## What is Vagrant?

It's software that is used to configure and manage VMs through the use of code in a Vagrantfile. Code is processed using Vagrant CLI.

### Installing Vagrant on Fedora
```bash
 sudo dnf install vagrant
```

