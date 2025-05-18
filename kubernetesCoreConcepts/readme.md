## **Core Concepts**

### Monolithic vs Microservices
   Monolithic Definition: The entire application’s functionality (UI, backend logic, data access) is built as a single, unified codebase.
   
   Microservices Definition: The application is split into small, independent services, each responsible for a specific feature or functionality.
# Kubernetes Architecture Explained

This document explains the key components that make up the architecture of a Kubernetes cluster, in simple terms.


![Kubernetes Architecture Diagram](https://miro.medium.com/v2/resize:fit:1400/1*0Sudxeu5mQyN3ahi1FV49A.png)


## Control Plane (Master Node Components)

### API Server

This is the "front desk" of Kubernetes. Whenever you want to interact with your cluster, your request goes through the API Server. It validates and processes these requests to the backend components.

### etcd

Think of this as the "database" of Kubernetes. It stores all the information about your cluster—what nodes are part of the cluster, what pods are running, what their statuses are, and more.

### Scheduler

The "event planner" for your containers. When you ask for a container to be run, the Scheduler decides which machine (Node) in your cluster should run it. It considers resource availability and other constraints while making this decision.

### Controller Manager

Imagine a bunch of small robots that continuously monitor the cluster to make sure everything is running smoothly. If something goes wrong (e.g., a Pod crashes), they work to fix it, ensuring the cluster state matches your desired state.

### Cloud Controller Manager

This is a specialized component that allows Kubernetes to interact with the underlying cloud provider, like AWS or Azure. It helps in tasks like setting up load balancers and persistent storage.

---

## Worker Node Components

### kubelet

This is the "manager" for each worker node. It ensures all containers on the node are healthy and running as they should be.

### kube-proxy

Think of this as the "traffic cop" for network communication either between Pods or from external clients to Pods. It helps in routing the network traffic appropriately.

### Container Runtime

This is the software used to run containers. Docker is commonly used, but other runtimes like containerd can also be used.

---

## Other Components

### Pod

The smallest unit in Kubernetes, a Pod is a group of one or more containers. Think of it like an apartment in an apartment building.

### Service

This is like a phone directory for Pods. Since Pods can come and go, a Service provides a stable "address" so that other parts of your application can find them.

### Volume

This is like an external hard-drive that can be attached to a Pod to store data.

### Namespace

A way to divide cluster resources among multiple users or teams. Think of it as having different folders on a shared computer, where each team can only see their own folder.

### Ingress

Think of this as the "front door" for external access to your applications, controlling how HTTP and HTTPS traffic should be routed to your services.




### Commands
---
1. `kubectl cluster-info`  
   - Displays cluster information to understand the Kubernetes architecture.

---

### Kubectl and Pods and Namespaces

### 1. Namespace Commands

2. `kubectl get namespaces`  
   - Lists all namespaces in the cluster.

3. `kubectl get ns`  
   - Shorthand for listing all namespaces.

4. `kubectl create ns <your-namespace>`  
   - Creates a new namespace with the specified name.

5. `kubectl delete namespace <namespace-name>`  
   - Deletes the specified namespace and all resources inside it.

6. `kubectl create namespace monitoring`  
   - Creates a namespace for monitoring resources.

7. `kubectl label namespace monitoring team=devops`  
   - Adds a label to the monitoring namespace.

8. `kubectl describe namespace monitoring`  
   - Displays detailed information about the monitoring namespace.

---

### 2. Pod Commands

9. `kubectl run nginx --image=nginx`  
   - Creates a Pod named 'nginx' using the nginx image from CLI.

10. `kubectl get pods`  
    - Lists all Pods in the current namespace.

11. `kubectl get pods -n <your-namespace>`  
    - Lists all Pods in the specified namespace.

12. `kubectl get pods -n <your-namespace> -o wide`  
    - Lists all Pods in the specified namespace with more detailed info.

13. `kubectl delete pod <pod-name> -n <your-namespace>`  
    - Deletes the specified Pod from the given namespace.

14. `kubectl describe pod nginx -n nginx`  
    - Displays detailed information about the nginx Pod.
