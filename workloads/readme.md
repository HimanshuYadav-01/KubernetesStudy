# Kubernetes Workloads 

This document explains the core Kubernetes workload resources including **Deployments**, **StatefulSets**, **DaemonSets**, **ReplicaSets**, **Jobs**, and **CronJobs**. It covers their definitions, key characteristics, and common `kubectl` commands to manage them.

---

## 1. Deployments

### Definition
A **Deployment** manages a set of identical Pods and ensures that the specified number of replicas are running at all times. It provides declarative updates for Pods and ReplicaSets.

### Characteristics
- Supports **rolling updates** to update Pods without downtime.
- Manages ReplicaSets under the hood.
- Enables easy rollback to previous versions.
- Declarative updates via YAML manifests.

### Common Commands

| Command                                        | Description                                   |
|-----------------------------------------------|-----------------------------------------------|
| `kubectl apply -f deployment.yml`              | Deploy a workload defined in deployment.yml.  |
| `kubectl delete deployment <deployment-name>` | Delete a deployment and its Pods.              |
| `kubectl get deployments`                      | List all deployments in the current namespace.|
| `kubectl describe deployment <deployment-name>`| Show detailed info about a deployment.         |
| `kubectl get pods -o wide`                      | List Pods with extended info (IP, node, etc). |
| `kubectl exec -it <pod-name> -- /bin/bash`    | Enter inside a Pod container shell.             |
| `kubectl scale deployment <deployment-name> --replicas=3` | Scale deployment to 3 replicas.        |

---

## 2. StatefulSets

### Definition
A **StatefulSet** manages stateful applications, providing guarantees about the ordering and uniqueness of Pods.

### Characteristics
- Stable, unique network identities for Pods.
- Stable persistent storage using PersistentVolumeClaims.
- Ordered, graceful deployment and scaling.
- Ordered rolling updates.

### Common Commands

| Command                                         | Description                                  |
|------------------------------------------------|----------------------------------------------|
| `kubectl apply -f statefulset.yml`              | Deploy a StatefulSet defined in statefulset.yml. |
| `kubectl delete statefulset <name>`             | Delete a StatefulSet and its Pods.           |
| `kubectl describe statefulset <name> -n <ns>`  | Show detailed info about a StatefulSet.      |
| `kubectl get statefulsets`                      | List all StatefulSets in the namespace.      |

---

## 3. DaemonSets

### Definition
A **DaemonSet** ensures that a copy of a Pod runs on **all (or some)** nodes in the cluster, often used for logging or monitoring agents.

### Characteristics
- Runs exactly one Pod per eligible node.
- Automatically adds Pods to new nodes joining the cluster.
- Useful for cluster-wide agents (e.g., Fluentd, Prometheus exporters).

### Common Commands

| Command                                      | Description                                  |
|---------------------------------------------|----------------------------------------------|
| `kubectl apply -f daemonset.yml`             | Deploy a DaemonSet.                          |
| `kubectl delete daemonset <name>`            | Delete a DaemonSet and its Pods.            |
| `kubectl describe daemonset <name> -n <ns>` | Show detailed info about a DaemonSet.       |
| `kubectl get daemonsets`                      | List all DaemonSets in the namespace.       |

---

## 4. ReplicaSets

### Definition
A **ReplicaSet** ensures that a specified number of Pod replicas are running at any given time.

### Characteristics
- Provides self-healing by replacing failed Pods.
- Usually managed by Deployments directly.
- Can be used standalone for basic replication needs.

### Common Commands

| Command                                      | Description                                   |
|---------------------------------------------|-----------------------------------------------|
| `kubectl apply -f replicaset.yml`             | Deploy a ReplicaSet.                          |
| `kubectl delete replicaset <name>`            | Delete a ReplicaSet and its Pods.            |
| `kubectl describe replicaset <name> -n <ns>` | Show detailed info about a ReplicaSet.       |
| `kubectl get replicasets`                      | List all ReplicaSets in the namespace.       |

---

## 5. Jobs and CronJobs

### Jobs

- **Job** runs one or more Pods to completion (batch processing).
- It ensures that a specified number of Pods successfully terminate.

### CronJobs

- **CronJob** schedules Jobs to run periodically at fixed times or intervals, similar to cron jobs in Linux.

### Common Commands

| Command                             | Description                               |
|------------------------------------|-------------------------------------------|
| `kubectl apply -f job.yml`          | Deploy a Job defined in job.yml.          |
| `kubectl delete job <name>`         | Delete a Job and its Pods.                 |
| `kubectl get jobs`                  | List all Jobs in the namespace.            |
| `kubectl apply -f cronjob.yml`      | Deploy a CronJob to schedule recurring tasks. |
| `kubectl delete cronjob <name>`     | Delete a CronJob.                          |
| `kubectl get cronjobs`              | List all CronJobs in the namespace.        |

---

## Example Commands Summary

```bash
# Deploy workloads
kubectl apply -f deployment.yml
kubectl apply -f statefulset.yml
kubectl apply -f daemonset.yml
kubectl apply -f replicaset.yml
kubectl apply -f job.yml
kubectl apply -f cronjob.yml

# Delete workloads
kubectl delete deployment <name>
kubectl delete statefulset <name>
kubectl delete daemonset <name>
kubectl delete replicaset <name>
kubectl delete job <name>
kubectl delete cronjob <name>

# Inspect workloads
kubectl get deployments
kubectl get statefulsets
kubectl get daemonsets
kubectl get replicasets
kubectl get jobs
kubectl get cronjobs

kubectl describe deployment <name>
kubectl describe statefulset <name> -n <namespace>
kubectl describe daemonset <name> -n <namespace>
kubectl describe replicaset <name> -n <namespace>

# Scaling deployments
kubectl scale deployment <deployment-name> --replicas=3 -n <namespace>

# Exec into pod
kubectl exec -it <pod-name> -- /bin/bash

# Get pods with wide info
kubectl get pods -o wide
