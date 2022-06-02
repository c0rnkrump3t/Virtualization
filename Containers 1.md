# Containers:
---

## What is a Container?
A container is a isolated group of  processes that run on a single host and acts as a complete application. Containers do not have an OS or kernel.
![[Pasted image 20220601233830.png]]

## How do Containers work?
Containers are based on functions that the kernel uses to isolate applications. Though the applications are isolated they belong to a similar Linux environment. A Linux Container Daemon (LXD) is used to run containers on the same system. LXCs are container based virtualization technologies that function at the OS level and can help automate mass container management. Each container is based on the file system. Containers are scalable and can be managed by orchestration systems like Apache Mesos and Google Kubernetes.
```bash
sudo dnf install --refresh
```


## 