## Creating the Kubernetes pods

There are two ways to create Kubernetes pods.

1. Imperative Method: In the imperative method the commands are executed directly in order to create or manage the resources.
```bash
kubectl run <pod name> --image=<image name>
```
![Image](https://github.com/user-attachments/assets/ec027d5f-36a0-4772-8d1c-f5f187820abf)

This method is quick but the main problems are it is not reusable or version controllable.

### How to get the YAML from the created pod

```bash
kubectl get pod <pod name> -o yaml > <pod name>.yaml
```

2. Declarative Method: The declarative approach involves defining the desired state of resources in YAML or JSON files. These files can be stored in version control for better management. 

Example YAML File: 

```bash
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
  - name: nginx
    image: nginx  
```
![Image](https://github.com/user-attachments/assets/8c5e137b-84e0-4e6e-a4af-830a10fda24b)

### 🌐 References
1. [YouTube Video](https://www.youtube.com/watch?v=_f9ql2Y5Xcc&t=509s)
2. [Kubernetes Documentation: Pod Lifecycle](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/)
3. [Kubernetes Troubleshooting Guide: Debugging Pods](https://kubernetes.io/docs/tasks/debug/debug-application/)
