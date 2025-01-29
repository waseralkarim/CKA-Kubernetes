# Kubernetes Services

In the kubernetes dynamic environment the pod created, destroyed and rescheduled. Kubernetes services provide us with proper endpoint. Services are essential for enabling reliable communication between Pods and external clients

## Types of Services

ClusterIP: The default service type. Exposes the service on a cluster-internal IP, making it only reachable within the cluster.

NodePort: Exposes the service on each Node's IP at a static port. This allows external access to the service.

LoadBalancer: Exposes the service externally using a cloud provider's load balancer. Automatically creates NodePort and ClusterIP services.

External: Maps a service to a DNS name.