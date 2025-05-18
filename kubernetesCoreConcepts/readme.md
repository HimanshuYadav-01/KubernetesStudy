## **Core Concepts**

### Monolithic vs Microservices, Kubernetes Architecture

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
