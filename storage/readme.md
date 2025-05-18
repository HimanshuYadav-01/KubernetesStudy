
# 📦 Kubernetes: Storage and Configuration Management

## 📁 Persistent Volumes (PV)

### 🔹 What is a Persistent Volume?

A **PersistentVolume (PV)** is a cluster-wide resource that provides storage to pods. It can be provisioned manually by the admin or dynamically using a StorageClass. PVs are independent of the pod lifecycle.

### ✅ Basic Commands

```bash
kubectl apply -f persistentVolume.yml        # Create a PersistentVolume
kubectl get pv                               # List all PersistentVolumes
kubectl describe pv <pv-name>                # View detailed information about a PV
```

---

## 📄 Persistent Volume Claims (PVC)

### 🔹 What is a Persistent Volume Claim?

A **PVC** is a user request for storage. Kubernetes matches it with a suitable PV and binds it. This allows pods to request storage without knowing how it's provisioned.

### ✅ Basic Commands

```bash
kubectl apply -f persistentVolumeClaim.yml   # Request storage through a PersistentVolumeClaim
kubectl get pvc                              # List all PVCs
kubectl describe pvc <pvc-name>              # View detailed information about a PVC
```

---

## 📂 StorageClasses

### 🔹 What is a StorageClass?

A **StorageClass** defines a type of storage available in the cluster (e.g., fast SSD, standard HDD). When PVCs reference a StorageClass, Kubernetes dynamically provisions a matching PV.

### ✅ Basic Commands

```bash
kubectl get storageclass                     # List all storage classes available in the cluster
kubectl describe storageclass <class-name>   # Get details of a specific StorageClass
```

### 📚 Types of StorageClasses

| Type       | Description                                             |
| ---------- | ------------------------------------------------------- |
| `standard` | Default class for many clusters                         |
| `gp2/gp3`  | AWS EBS General Purpose SSD                             |
| `premium`  | Azure Premium Managed Disk                              |
| `fast`     | High-performance storage (e.g., SSDs on GCP)            |
| `manual`   | Manually created PVs for static provisioning            |
| `none`     | Used when provisioning is not required (headless usage) |

> ℹ️ Dynamic provisioning simplifies storage operations by automatically creating PVs when PVCs request them.

---

## ⚙️ ConfigMaps

### 🔹 What is a ConfigMap?

A **ConfigMap** stores non-sensitive configuration data such as environment variables, app settings, or CLI arguments. It helps in separating configuration from application logic.

### ✅ Basic Commands

```bash
kubectl create configmap app-config --from-file=config.properties  # Create a ConfigMap from a file
kubectl apply -f configmap.yml                                     # Create a ConfigMap from YAML
kubectl get configmaps                                             # List all ConfigMaps
kubectl describe configmap <name>                                  # View detailed information about a ConfigMap
```

> 🧠 Use ConfigMaps to manage and inject configurations into containers without rebuilding the image.

---

## 🔐 Secrets

### 🔹 What is a Secret?

A **Secret** is used to store sensitive information (like passwords, tokens, SSH keys) in base64-encoded form. It ensures sensitive data is not exposed directly in the pod specs.

### ✅ Basic Commands

```bash
kubectl create secret generic db-credentials --from-literal=username=admin --from-literal=password=admin123  # Create a Secret with database credentials
kubectl apply -f secret.yml                                                                             # Create a Secret from YAML
kubectl get secrets                                                                                     # List all Secrets
kubectl describe secret <name>                                                                          # View detailed information about a Secret
```

> ⚠️ Note: While Secrets are base64-encoded, they are **not encrypted** by default. Use external secret management tools for enhanced security.

---

## ✅ Final Tip

Keep all your YAML files in a folder like `k8s-yamls/` and apply them using:

```bash
kubectl apply -f ./k8s-yamls/
```

---

🧡 Happy Kubernetes-ing!
