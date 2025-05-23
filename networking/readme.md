# Kubernetes Networking 

This document covers the core concepts of Kubernetes networking, including **Cluster Networking**, **Services**, **Ingress**, and **Network Policies**. It also provides common commands to manage these resources.

---

## 1. Cluster Networking

### Definition
Cluster Networking allows communication between Pods, Services, and external clients. It provides the foundation for service discovery and load balancing within the Kubernetes cluster.

### Common Command

| Command                 | Description                     |
|-------------------------|---------------------------------|
| `kubectl get svc -A`     | List all services in the cluster (across all namespaces). |

---

## 2. Services

### Definition
A **Service** exposes a set of Pods as a network service, enabling stable access regardless of Pod lifecycle. It abstracts the Pods and provides load balancing and a fixed IP or DNS name.

### Types of Services

| Type             | Description                                                                                     |
|------------------|-------------------------------------------------------------------------------------------------|
| **ClusterIP**    | Default type; exposes service on a cluster-internal IP. Accessible only within the cluster.      |
| **NodePort**     | Exposes the service on each Node’s IP at a static port. Accessible outside the cluster via `<NodeIP>:<NodePort>`. |
| **LoadBalancer** | Exposes the service externally using a cloud provider’s load balancer.                          |
| **ExternalName** | Maps the service to the contents of the externalName field (e.g., `example.com`).               |
| **Headless Service (ClusterIP: None)** | Does **not** allocate a ClusterIP. Used for direct Pod access and service discovery via DNS without load balancing. |

---

## 3. Ingress

### Definition
An **Ingress** is a Kubernetes resource that manages external access to services, typically HTTP/HTTPS, providing routing rules, SSL termination, and virtual hosting.

### Common Commands

| Command                                  | Description                           |
|-----------------------------------------|-------------------------------------|
| `kubectl apply -f ingress.yml`            | Create or update an Ingress resource. |
| `kubectl describe ingress <ingress-name> -n <namespace>` | Show detailed information about an Ingress. |

---

## 4. Network Policies

### Definition
**Network Policies** control the communication between Pods and/or namespaces. They provide fine-grained traffic rules to restrict or allow network traffic.

### Common Commands

| Command                                  | Description                             |
|-----------------------------------------|---------------------------------------|
| `kubectl apply -f networkpolicy.yml`      | Create or update a Network Policy.    |
| `kubectl describe networkpolicy <name> -n <namespace>` | Show detailed info about a Network Policy. |

---

## Example Commands Summary

```bash
# Cluster Networking
kubectl get svc -A

# Services
kubectl apply -f service.yml
kubectl describe svc nginx-service -n nginx
kubectl get svc

# Ingress
kubectl apply -f ingress.yml
kubectl describe ingress nginx-ingress -n nginx
kubectl get ingress

# Network Policies
kubectl apply -f networkpolicy.yml
kubectl describe networkpolicy <name> -n <namespace>
kubectl get networkpolicy
