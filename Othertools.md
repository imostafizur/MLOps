## 🧪 Local Kubernetes Setup

This project is configured with the following Kubernetes tools installed:

### ✅ Installed Tools

- **Minikube**: `v1.35.0`  
  > Currently active and running the cluster (`kubectl config current-context` = `minikube`)

- **kind (Kubernetes IN Docker)**: `v0.29.0`  
  > Installed but **not currently in use**

### ❌ Not Installed

- `k3s`: Not found in system path
- `microk8s`: Not found in system path

### 🔧 Current Kubernetes Context

```bash
kubectl config get-contexts
