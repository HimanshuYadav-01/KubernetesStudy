```
# Kubernetes Scaling & Scheduling – Quick Guide

This document includes concise explanations and commonly used `kubectl` commands for Kubernetes scaling and scheduling features like HPA, VPA, Node Affinity, Taints and Tolerations, ResourceQuotas, and LimitRanges.

---

## 🔁 Horizontal Pod Autoscaler (HPA)

Automatically scales the number of pods in a deployment based on CPU utilization or custom metrics.

**Commands:**
```bash
kubectl autoscale deployment <deployment-name> --cpu-percent=50 --min=1 --max=5
kubectl get hpa
kubectl describe hpa <hpa-name>
```

---

## ⬆️ Vertical Pod Autoscaler (VPA)

Automatically adjusts pod CPU and memory **requests/limits** based on actual usage over time.

**Commands:**
```bash
kubectl get vpa
kubectl describe vpa <vpa-name>
```

---

## 📌 Node Affinity

Helps schedule pods onto specific nodes using label selectors.

**Commands:**
```bash
kubectl label node <node-name> disktype=ssd
kubectl get nodes --show-labels
kubectl describe pod <pod-name>
```

---

## 🚫 Taints and Tolerations

Used to repel pods from specific nodes unless they tolerate the taint.

**Commands:**
```bash
kubectl taint nodes <node-name> key=value:NoSchedule
kubectl taint nodes <node-name> key:NoSchedule-     # remove taint
kubectl describe node <node-name>
kubectl describe pod <pod-name>
```

---

## 📊 ResourceQuota

Restricts total resource usage (CPU, memory, pods, etc.) in a namespace.

**Commands:**
```bash
kubectl get resourcequota -n <namespace>
kubectl describe resourcequota <name> -n <namespace>
kubectl create quota <name> --hard=cpu=2,memory=1Gi,pods=4 -n <namespace>
```

---

## 📏 LimitRange

Sets default/min/max CPU and memory usage per container in a namespace.

**Commands:**
```bash
kubectl get limitrange -n <namespace>
kubectl describe limitrange <name> -n <namespace>
kubectl create limitrange <name> \
  --namespace=<namespace> \
  --default-cpu=200m --default-memory=256Mi \
  --default-request-cpu=100m --default-request-memory=128Mi
```

---

## ✅ Summary Table

| Feature             | Purpose                                           | Key Commands                             |
|---------------------|---------------------------------------------------|------------------------------------------|
| HPA                 | Auto-scale pods based on CPU/metrics              | `kubectl autoscale`, `kubectl get hpa`   |
| VPA                 | Auto-tune resource requests/limits                | `kubectl get vpa`, `kubectl describe vpa`|
| Node Affinity       | Schedule pods to matching labeled nodes           | `kubectl label`, `kubectl describe pod`  |
| Taints/Tolerations  | Control where pods are allowed/scheduled          | `kubectl taint`, `kubectl describe node` |
| ResourceQuota       | Limit total resources per namespace               | `kubectl get/describe resourcequota`     |
| LimitRange          | Set default resource limits per container         | `kubectl get/describe limitrange`        |

---
