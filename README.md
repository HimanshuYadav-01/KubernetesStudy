# KubernetesStudy

## 📘 How to Use

To make the most of this repository, **go through this `README.md` file to navigate the folders and files properly**. Each directory contains relevant Kubernetes concepts with YAML manifests and explanations to guide your learning and implementation.

## 🔧 Prerequisites

- Basic understanding of Kubernetes
- A working Kubernetes cluster (Minikube, KIND, GKE, etc.)
- `kubectl` configured and working

---

# 📦 KubernetesCoreConcepts

Welcome to the **KubernetesCoreConcepts** repository! This project is organized to help you understand and practice the core components of Kubernetes with proper YAML examples and detailed explanations.


---

## 🧭 Suggested Navigation

1. Start with `workloads/` to understand core resources used to run and manage containers.
2. Move to `storage/` to learn about data persistence and secrets management.
3. Finally, explore `networking/` to grasp how communication and routing work in Kubernetes.

---


## 📁 Folder Structure

### 1. `workloads/` 🏗️  
This directory contains Kubernetes workloads YAML files and explanations for:

- **Deployment**  
- **ReplicaSet**  
- **DaemonSet**  
- **Namespace**  
- **Job**  
- **CronJob**  
- **StatefulSet**

Each concept is paired with a YAML file and a short description to explain its purpose and usage.

---

### 2. `storage/` 💾  
This folder focuses on Kubernetes storage concepts, complete with YAML examples and use-cases:

- **PersistentVolume (PV)**
- **PersistentVolumeClaim (PVC)**
- **ConfigMap**
- **Secrets**
- **StorageClasses**
- **configMap**
- **Secrets**

Understand how Kubernetes handles data, secrets, and configurations effectively.

---

### 3. `networking/` 🌐  
Networking plays a vital role in Kubernetes. This folder includes:

- **service.yml** – Example and explanation of different service types (ClusterIP, NodePort, LoadBalancer)
- **ingress.yml** – YAML and explanation for Ingress resources
- **Cluster Networking** – How pods communicate in the cluster
- **Network Policies** – Rules to control traffic
- **Types of Services** – Detailed overview of ClusterIP, NodePort, LoadBalancer, and Headless services
- **ingress.yml** - Defines Ingress resource to route external traffic to internal services using hostname/path-based rules
---

### 4. `scheduling-resources/` ⚙️  
Contains manifests for Kubernetes scheduling and resource management:

- **hpa.yml** – Horizontal Pod Autoscaler to auto-scale pods based on CPU/memory usage.  
- **vpa.yml** – Vertical Pod Autoscaler to adjust pod resource requests dynamically.  
- **node-affinity.yml** – Rules to control pod placement based on node labels.  
- **taints-tolerations.yml** – Allows pods to run on nodes with specific taints.  
- **resource-quota.yml** – Limits resource usage per namespace to prevent overconsumption.  
- **limit-range.yml** – Sets default resource requests and limits for containers in a namespace.
- **probes.yml** – Its checks whether server is ready to serve , restarts pod depending of type of probe configuration.

---
