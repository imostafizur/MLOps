## ⚙️ Kubeflow Components Installed

This project includes a partial Kubeflow deployment focused on **Katib**, the hyperparameter tuning component.

### ✅ Running Components (Namespace: `kubeflow`)

| Component         | Pod Name Prefix          | Description |
|------------------|--------------------------|-------------|
| Katib Controller | `katib-controller-*`     | Manages Katib experiments and trial lifecycles |
| Katib DB Manager | `katib-db-manager-*`     | Handles communication between Katib and the MySQL backend |
| Katib MySQL      | `katib-mysql-*`          | Stores experiment metadata |
| Katib UI         | `katib-ui-*`             | Web interface to manage and visualize Katib experiments |

> All components are running in the `kubeflow` namespace.

---

### ❌ Not Installed

The following core Kubeflow components are **not currently deployed**:

- Kubeflow Central Dashboard  
- Kubeflow Pipelines  
- Notebooks / Notebook Controller  
- KServe / Model Serving  
- Metadata Store  
- Profiles / Multi-user Support  

---

### 🔍 To Check Kubeflow Components

Run:
```bash
kubectl get pods -n kubeflow
