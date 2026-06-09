# Kubernetes GitOps Observability

GitOps repo for cluster observability managed by Argo CD.

## Apps

- `kube-prometheus-stack`: Prometheus Operator, Prometheus, Alertmanager, Grafana, node-exporter, kube-state-metrics

## Argo CD

Apply the app manifest after Argo CD is installed:

```bash
kubectl apply -f argocd/apps/kube-prometheus-stack.yaml
```

The application uses automated sync and server-side apply for CRD-heavy resources.
