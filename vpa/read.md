
# 📈 Kubernetes Vertical Pod Autoscaler (VPA) Demo

## 📖 What is VPA in Kubernetes?

**Vertical Pod Autoscaler (VPA)** automatically adjusts the **CPU and memory requests and limits** for containers in your pods based on usage. Unlike HPA (which scales pods horizontally by increasing replicas), **VPA optimizes individual pod resources vertically** — ideal for workloads where scaling out is not efficient or feasible.

---

## ⚙️ Prerequisites

1. A running Kubernetes cluster (e.g., Kubeadm via KillerCoda)
2. Metrics Server installed and working
3. `kubectl` access with proper context set
4. Internet access from cluster nodes (for pulling container images)

---

## 📦 Step-by-Step Setup for VPA Demo

### ✅ 1. Install the Metrics Server (if not already installed)

```bash
git clone https://github.com/kubernetes/autoscaler.git
cd autoscaler/vertical-pod-autoscaler
git checkout origin/vpa-release-1.0
REGISTRY=registry.k8s.io/autoscaling TAG=1.0.0 ./hack/vpa-process-yamls.sh apply
```

