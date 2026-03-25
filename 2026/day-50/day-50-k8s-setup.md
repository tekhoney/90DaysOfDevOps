# Day 50 – Kubernetes Architecture and Cluster Setup

## Task 1: Recall the Kubernetes Story
### Why was Kubernetes created? What problem does it solve that Docker alone cannot?

   Kubernetes was created to manage the containers (Auto scaling, self healing), that is why it is called orchatrator tool, Docker can run one container at a time docker can cause downtime at the time of patching or rolling or rollback while kubernetes ensures zero downtime because it can manage thousands of containers. 
   
### Who created Kubernetes and what was it inspired by?

In 2014 google create a tool named **BURG** which was developed for auto scaling and auto healing the servers while heavy traffic on it. after that it was donated to the CNCF (cloud native computing foundation) and made it open source, renamed as **KUBERNETES**, it is a containerisation tool

### What does the name "Kubernetes" mean?

Kubernetes means ship pilot, we can remember as Docker creates the container and kubernets manage the containers.

# Task 2: Draw the Kubernetes Architecture

## Architecture Link 

https://miro.com/app/board/uXjVGsBPz58=/?share_link_id=911991386229

### Control Plane (Master Node):

API Server — the front door to the cluster, every command goes through it
etcd — the database that stores all cluster state
Scheduler — decides which node a new pod should run on
Controller Manager — watches the cluster and makes sure the desired state matches reality

### Worker Node:

kubelet — the agent on each node that talks to the API server and manages pods
kube-proxy — handles networking rules so pods can communicate
Container Runtime — the engine that actually runs containers (containerd, CRI-O)

After drawing, verify your understanding:

What happens when you run kubectl apply -f pod.yaml? Trace the request through each component.

This command is to create the pod "pod.yml", API server will ask to scheduler to create a new pod "pod.yml" scheduler will ask to etcd about the pod state. if not presented, it will tell to Api server to create a new pod in worker nod.

What happens if the API server goes down?

If API server gets down no command will run and it will halt the process, 

What happens if a worker node goes down

As we understood the all the pods created and works at worker node and docker container runs unside the pod, no pod will running if worker node get down.

## Task 3: Install kubectl

history
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl

opstree@opstree-Latitude-3420:~/devops/kubernetes-practise$ kubectl version
Client Version: v1.35.2
Kustomize Version: v5.7.1
Server Version: v1.35.0

## Task 4: Set Up Your Local Cluster

Option A: kind (Kubernetes in Docker)

[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.31.0/kind-linux-amd64
  # For ARM64
  [ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.31.0/ki
  chmod +x ./kind
  sudo mv ./kind /usr/local/bin/kind

  opstree@opstree-Latitude-3420:~/devops/kubernetes-practise$ kind --version
kind version 0.31.0

## Creating a cluster

### vim kind-config.yml 
### kind: Cluster
### apiVersion: kind.x-k8s.io/v1alpha4
### name: krishan-cluster
 
### nodes:
###  - role: control-plane
 ###   image: kindest/node:v1.35.0
 
###  - role: worker
###    image: kindest/node:v1.35.0
  
###  - role: worker
###    image: kindest/node:v1.35.0
  
###  - role: worker
###    image: kindest/node:v1.35.0
   
