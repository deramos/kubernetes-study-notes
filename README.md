# Kubernetes-and-MLOps-notes
Study notes on K8 and MLOps

## Introduction to Pods
Each Kubernetes cluster consists of master and worker nodes. Each worker node is made up of:
- Docker
- Kubelet
- Kube-proxy
Worker nodes contain everything required to run pods,and reports back to the master node.
Pods contain one more docker containers pulled from a registry, and combined into a "super container".
- Namespaces are used to create virtual clusters that can be run concurrently with other clusters in 
a physical machine. 