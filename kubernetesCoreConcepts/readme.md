## **Core Concepts**

### Monolithic vs Microservices, Kubernetes Architecture

1. `kubectl cluster-info`  
   Display cluster information to understand the Kubernetes architecture.



### Kubectl and Pods and Namespaces


### 1. Namespace Commands

```bash
1. kubectl get namespaces
```
- Lists all namespaces in the cluster.

```bash
2. kubectl get ns
```
- Shorthand for listing all namespaces.

```bash
3. kubectl create ns <your-namespace>
```
- Creates a new namespace with the specified name.

```bash
4. kubectl delete namespace <namespace-name>
```
- Deletes the specified namespace and all resources inside it.
`kubectl create namespace monitoring`  
   Create a namespace for monitoring resources.

3. `kubectl label namespace monitoring team=devops`  
   Add a label to the monitoring namespace.
4. `kubectl describe namespace monitoring`  
   Display detailed information about the monitoring namespace.

---

### 2. Pod Commands

```bash
5. kubectl run nginx --image=nginx
```
- Creates a Pod named 'nginx' using the nginx image from CLI.

```bash
6. kubectl get pods
```
- Lists all Pods in the current namespace.

```bash
7. kubectl get pods -n <your-namespace>
```
- Lists all Pods in the specified namespace.

```bash
8. kubectl get pods -n <your-namespace> -o wide
```
- Lists all Pods in the specified namespace with more detailed info.

```bash
9. kubectl delete pod <pod-name> -n <your-namespace>
```
- Deletes the specified Pod from the given namespace.

 `kubectl describe pod nginx -n nginx`  
   Display detailed information about the nginx pod.



