# Kubernetes Replication Controller, Replica Set and Deployment

## 1. Replication Controller

If the pod which we created gets deleted or currupted the replication controller helps us to provision new pods automatically. The number of pods are specified in the yaml or json file. For example:

```bash
apiVersion: v1
kind: ReplicationController
metadata:
  name: nginx-rc
  labels:
    env: demo
spec:
  replicas: 3
  selector:
    env: demo
  template:
    metadata:
      name: nginx-pod
      labels:
        env: demo
        type: frontend
    spec:
      containers:
        - name: nginx-container
          image: nginx
          ports:
            - containerPort: 80
```
In the `replicas: 3` section, we specified 3 replica pod should run at all time. If a pod crashes or is deleted, the RC automatically creates a new one to maintain the desired state.

## 2. Replica Set

ReplicaSet is the next evolution of the Replication Controller. It works like same as RC but introduces a more flexible selector mechanism, allowing us to use expressions for matching pods.

Example: 

```bash
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nginx-rs
  labels:
    env: demo
spec:
  replicas: 1
  selector:
    env: demo
  template:
    metadata:
      name: nginx-pod
      labels:
        env: demo
        type: frontend
    spec:
      containers:
        - name: nginx-container
          image: nginx
          ports:
            - containerPort: 80
```
> [!NOTE]
> typically replica set is managed indirectly through deployments.

## 3. Deployment

A Deployment builds on ReplicaSet and adds declarative updates for pods and ReplicaSets. It’s the preferred way to manage stateless applications in Kubernetes. Deployments support rolling updates, rollbacks, and scaling.

Example: 

```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deploy
  labels:
    env: demo
spec:
  template:
    metadata:
      name: nginx
      labels:
        env: demo
    spec:
      containers:
        - name: nginx
          image: nginx
          ports:
            - containerPort: 80
  replicas:  3
  selector:
    matchLabels:
      env: demo  
```

## 🛠️ 3 Ways to update the replica numbers:
1. Directly through YAML/JSON file
2. Live update: Kubectl edit rs/<pod name>
3. Imperative way: kubectl scale --replicas=<number of replicas> rs/<pod name>

### 🌐 References
1. [Replication Controller - Kubernetes Docs](https://kubernetes.io/docs/concepts/workloads/controllers/replicationcontroller/)
2. [ReplicaSet - Kubernetes Docs](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/)
3. [Deployment - Kubernetes Docs](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
