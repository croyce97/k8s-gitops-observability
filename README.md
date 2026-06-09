# Kubernetes GitOps Observability

GitOps repo for cluster observability managed by Argo CD.

## Apps

- `kube-prometheus-stack`: Prometheus Operator, Prometheus, Alertmanager, Grafana, node-exporter, kube-state-metrics
- `ingress-nginx`: hostNetwork ingress controller for the EC2 kubeadm cluster
- `external-dns`: Route53 DNS records for public ingress hosts
- `cert-manager`: certificate controller required by Rancher
- `rancher`: Rancher Manager
- `platform-ingresses`: Argo CD and Grafana ingress resources

## Domains

- `argocd.canhnq.online`
- `grafana.canhnq.online`
- `rancher.canhnq.online`

## Argo CD

Apply the app manifests after Argo CD is installed:

```bash
kubectl apply -f argocd/apps/
```

CRD-heavy applications use server-side apply where needed.
