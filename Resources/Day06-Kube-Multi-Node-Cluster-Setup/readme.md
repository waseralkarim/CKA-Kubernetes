##Kind 

kind is a tool for running local Kubernetes clusters using Docker container “nodes”.
kind was primarily designed for testing Kubernetes itself, but may be used for local development or CI.

### Installing kind

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/latest/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

```
### Verify installation:

`kind --version

### Creating a Cluster with kind

`kind create cluster

### Verify the cluster

`kubectl get nodes

