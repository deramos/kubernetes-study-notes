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

### Introduction to Masters
In production settings, there are usually three masters to establish a quorum for pod deployment
- Manages cluster nodes
- Masters manages pod scheduling and deployment
- There are three control panel components
  - the API server
  - controller manager server
  - etcd (which serves as a "database" to store cluster information)

### Pod Continuation
The reason why pods were "invented".
- In a typical microservice, each service might have a database that other services shouldn't have access to
  - However, you might want dependent services to have access to those internal DB (and other shared resources)
  - So why not bundle every dependent service (docker container) who might need access to a shared service
    - and call the packaging "pod". Each pod can container one or more docker container with access to shared resources
    - and exposes an API for other services to access the shared resources / perform operations on those pods
    - The APIs have an IP address and a port address


## Scheduler
The scheduler is created by the controller manager and uses etcd to look up the state of the cluster 
and which nodes to deploy a newly created pod in.
Etcd is a distributed key-value store that is very fast and monitors the state of the cluster
