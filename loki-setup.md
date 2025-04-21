
# Loki & Promtail Setup

## 1. Add Grafana Helm Repo
```bash
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
```

## 2. Install Loki Stack
```bash
helm install loki grafana/loki-stack -n monitoring
```

## 3. Check Loki Logs
```bash
kubectl logs -l app=loki -n monitoring
```

## 4. Explore Logs in Grafana
- Open Grafana at [http://localhost:3000](http://localhost:3000)
- Go to **Explore** tab
- Select **Loki** as data source
- Use a query like:
```logql
{job="kubernetes-pods"}
```

You’ll see logs from running pods!
