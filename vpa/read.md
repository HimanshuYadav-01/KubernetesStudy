
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

✅ 1. Install the Metrics Server (if not already installed)

```bash
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```

🔹 2. Patch the deployment to allow insecure TLS (required for some kubeadm setups like Minikube or VM-based clusters):
```bash
kubectl patch deployment metrics-server -n kube-system \
  --type='json' \
  -p='[{"op":"add","path":"/spec/template/spec/containers/0/args/-","value":"--kubelet-insecure-tls"}]'
```
3. Wait a few seconds and check the status:
```bash
kubectl get deployment metrics-server -n kube-system
kubectl get pods -n kube-system | grep metrics-server
```

4. Verify it works:
```bash
kubectl top node
kubectl top pod --all-namespaces
```


## ✅ 2. Deploy Apache Deployment & Service

### Create a namespace for Apache:

create deployment and service yml manifest.

## ✅ 3. Deploy Vertical Pod Autoscaler (VPA)
###  Clone the Kubernetes autoscaler repo:

```bash
git clone https://github.com/kubernetes/autoscaler.git
cd autoscaler/vertical-pod-autoscaler
git checkout origin/vpa-release-1.0
REGISTRY=registry.k8s.io/autoscaling TAG=1.0.0 ./hack/vpa-process-yamls.sh apply
```
## ✅ 4. Create VPA Object
Create apache-vpa.yaml:

## ✅ 5. Generate Load on Apache Pod
### Option 1: Generate HTTP traffic using busybox:
```bash
kubectl run apache-loadgen -n apache --image=busybox --restart=Never -it -- /bin/sh

while true; do wget -q -O- apache-service; done
```
### Option 2: Generate CPU load using stress:
```bash
kubectl run cpu-loader -n apache --image=progrium/stress -- /usr/bin/stress --cpu 2
```

## ✅ 6. View VPA Recommendations
### Check the VPA output:
```bash
kubectl describe vpa apache-vpa -n <your-namespace> 
watch kubectl top pods -n <your-namespace>
```
