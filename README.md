# Virtual Environment on Preprod using vCluster

This folder contains the configuration and Helm chart values to deploy a **vCluster** inside the `preprod` Kubernetes cluster. The goal is to provide **strong isolation** and allow developers or teams to work in their own virtual Kubernetes clusters without interfering with the shared control plane — especially when installing **global resources** like:

- CustomResourceDefinitions (CRDs)
- ClusterRoles and ClusterRoleBindings
- Admission webhooks
- APIService extensions

## 📌 Why Use vCluster?

When working in shared Kubernetes environments like `preprod`, installing global resources can lead to:

- Conflicts between teams or apps
- Security or compliance violations
- Resource pollution

By using **vCluster**, we simulate a fully isolated control plane **within a namespace**, giving each team or tenant their own:

- API Server
- etcd instance
- Controller Manager (optional)

This enables parallel testing of custom controllers, CRDs, or platform features safely and without cluster-wide impact.
