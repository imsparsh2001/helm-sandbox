# What is Helm?

## Helm: The APT for Kubernetes

Think of Helm as the "APT" or "YUM" for Kubernetes. Just like APT helps you manage software packages on a Linux system, Helm helps you manage applications on a Kubernetes cluster.

### How Helm Works:

In Linux, you use APT to install software like nginx by running:

```
sudo apt install nginx
```

This pulls the nginx package from a repository, installs it, and sets it up on your system.

In Kubernetes, you use Helm to install applications like nginx by running:

```
helm install my-nginx bitnami/nginx
```

This pulls an nginx Helm chart from a chart repository, creates the necessary Kubernetes resources (like deployments, services), and sets up the application in your cluster.

### Why Use Helm?

1. Package Management

APT manages DEB packages (like .deb files) on Linux.

Helm manages Helm Charts (YAML files bundled together) in Kubernetes.

2. Version Control

APT can install specific versions of a package using:

```
sudo apt install nginx=1.18.0
```

Helm can do the same:

```
helm install my-nginx bitnami/nginx --version 13.0.0
```

This means you can easily roll back or upgrade applications.

3. Configuration Management

With APT, you can configure software via config files (like /etc/nginx/nginx.conf).

With Helm, you can override configuration values using a YAML file:

```
helm install my-nginx bitnami/nginx --values custom-values.yaml
```

This allows you to customize how the application is deployed.

4. Managing Dependencies

APT automatically resolves dependencies between packages.

Helm handles dependencies between Kubernetes components, like ensuring a database is ready before deploying a web app.


### Why Helm Matters in Kubernetes

Kubernetes is a complex system with many moving parts (pods, deployments, services, etc.). Helm simplifies the process by packaging everything into reusable charts. It’s like having a one-click install for your entire application stack instead of manually creating each component.

# Understanding Helm Components


## 1. Helm Charts

A **Helm chart** is a collection of files that describe a set of Kubernetes resources. It acts as a **package** for your Kubernetes application, similar to a **DEB** or **RPM** file in Linux.

### **Components of a Chart:**

* **Chart.yaml:** Metadata about the chart (name, version, etc.).
* **values.yaml:** Default configuration values.
* **templates/**: Directory containing Kubernetes manifests as templates.
* **charts/**: Directory for chart dependencies.
* **README.md:** Optional documentation.

### **Creating a Chart:**

```bash
helm create myapp
```

This generates a new chart structure under the `myapp` directory.

### **Installing a Chart:**

```bash
helm install my-nginx bitnami/nginx
```

Charts enable you to define complex applications, including deployments, services, config maps, and more, all bundled together for easy management.

---

## 2. Helm Repositories

A **Helm repository** is a place where Helm charts are stored and shared. It’s similar to a **package repository** in Linux (like APT or YUM repos).

### **Adding a Repository:**

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
```

### **Listing Repositories:**

```bash
helm repo list
```

### **Updating Repositories:**

```bash
helm repo update
```

Repositories make it easy to organize, store, and distribute Helm charts, and they support versioning, so you can choose specific versions of a chart to install.

---

## 3. Helm Releases

A **Helm release** is a specific instance of a chart that has been deployed to your Kubernetes cluster. You can think of it as a **deployed version of your application.**

### **Creating a Release:**

```bash
helm install myapp ./myapp
```

### **Listing Releases:**

```bash
helm list
```

### **Upgrading a Release:**

```bash
helm upgrade myapp ./myapp
```

### **Rolling Back a Release:**

```bash
helm rollback myapp 1
```

### **Deleting a Release:**

```bash
helm uninstall myapp
```

Releases are useful for tracking deployed versions, performing rollbacks in case of failures, and managing multiple instances of the same chart.

---

## Summary

* **Charts** are packages that define Kubernetes resources.
* **Repositories** are storage locations for Helm charts.
* **Releases** are deployed instances of a chart.

