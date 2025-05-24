## 🧰 Kubernetes Components Installed

This Minikube-based cluster is running the following Kubernetes components:

### ✅ Control Plane Components

1. `kube-apiserver`  
   Handles all API requests and communication between components.

2. `kube-controller-manager`  
   Runs background processes that maintain the cluster state.

3. `kube-scheduler`  
   Assigns newly created pods to suitable nodes.

4. `etcd`  
   A distributed key-value store used to store all cluster data.

5. `kubelet`  
   Agent running on each node to ensure containers are healthy.

---

### ✅ Node Components

6. `kube-proxy`  
   Maintains network rules and handles traffic routing to pods.

---

### ✅ Add-ons / Extras

7. `dashboard`  
   Kubernetes Dashboard — web UI for managing cluster resources.

8. `kubectl port-forward`  
   For accessing the Dashboard via port `8888` from localhost.

---

> 📝 Note: This setup is running on a single-node Minikube cluster inside a GitHub Codespace.
