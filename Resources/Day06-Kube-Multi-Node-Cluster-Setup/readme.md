# Setting Up and Managing KIND Clusters

In this post, I document the process of setting up **Kubernetes in Docker (KIND)** clusters on my local machine, following the [KIND official documentation](https://kind.sigs.k8s.io/). This involves creating both single-node and multi-node clusters, installing `kubectl`, and verifying the setup.

---

## **1. Installing a Single-Node KIND Cluster**

To begin, I installed a single-node cluster using Kubernetes version **1.29**. 

```bash
kind create cluster --image kindest/node:v1.29.0 --name single-node-cluster

```
After verifying the setup with kubectl get nodes, the single-node cluster was successfully running.

## 2. Deleting the Single-Node Cluster
To practice cluster management, I deleted the single-node cluster:

```bash
kind delete cluster --name single-node-cluster
```
## 3. Creating a Multi-Node KIND Cluster
Next, I created a multi-node cluster named cka-cluster2 with:

1 Control Plane Node
3 Worker Nodes
Kubernetes Version 1.30
I used the following configuration file for this setup:

multi-node-cluster.yaml

```bash
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
name: cka-cluster2
nodes:
  - role: control-plane
  - role: worker
  - role: worker
  - role: worker
```
The cluster was created with:

```bash

kind create cluster --image kindest/node:v1.30.0 --config multi-node-cluster.yaml

```
## 4. Installing Kubectl
To manage the clusters, I installed kubectl using the [Kubernetes CLI installation guide](https://kubernetes.io/docs/tasks/tools/). After setting the context to the newly created cluster, I ran:

```bash
kubectl config use-context kind-cka-cluster2
kubectl get nodes

```
## 5. Verifying with Docker

Finally, I verified that the nodes were running as Docker containers:

```bash
docker ps

```
Each node (control plane and workers) appeared as a running container.

## 6. References 

- [KIND Documentation](https://kind.sigs.k8s.io/)  
- [Install Kubectl](https://kubernetes.io/docs/tasks/tools/)

