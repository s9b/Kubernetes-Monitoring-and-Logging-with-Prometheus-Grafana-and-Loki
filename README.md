
# Kubernetes Monitoring with Prometheus, Grafana, and Loki

## Prerequisites
- Docker Desktop with Kubernetes enabled
- kubectl
- Helm
- VS Code

## Quick Start

### 1. Add Helm Repos
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
```

### 2. Install Prometheus & Grafana
```bash
helm install monitoring prometheus-community/kube-prometheus-stack \
  -n monitoring --create-namespace \
  --set grafana.adminPassword='admin'
```

### 3. Check Pods
```bash
kubectl get pods -n monitoring
```

### 4. Port-Forward Grafana
```bash
kubectl port-forward svc/monitoring-grafana 3000:80 -n monitoring
```

Then access Grafana at: [http://localhost:3000](http://localhost:3000)  
Login: `admin / admin`
