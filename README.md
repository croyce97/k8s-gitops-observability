# Kubernetes GitOps Observability

Kubernetes GitOps lab for operating platform services with Argo CD. The goal is to keep cluster observability, ingress, DNS, certificates, and admin tooling reproducible from versioned manifests.

## Scope

| Area | Target |
| --- | --- |
| GitOps controller | Argo CD application manifests and sync policy |
| Observability | Prometheus Operator, Prometheus, Alertmanager, Grafana, node-exporter, kube-state-metrics |
| Ingress | NGINX ingress for public HTTP/S endpoints |
| DNS | ExternalDNS-managed Route53 records |
| TLS | cert-manager-managed certificates |
| Platform admin | Rancher Manager for cluster visibility |

## Repository layout

```text
.
├── argocd/
│   └── apps/          # Argo CD Application manifests
├── docs/              # Architecture notes and runbooks
└── README.md
```

## Expected domains

- `argocd.canhnq.online`
- `grafana.canhnq.online`
- `rancher.canhnq.online`

## Bootstrap

Install Argo CD first, then apply the application manifests:

```bash
kubectl apply -f argocd/apps/
```

CRD-heavy applications should use server-side apply where needed:

```bash
kubectl apply --server-side -f <manifest>
```

## Operating principles

- Keep generated secrets out of Git.
- Prefer small, reviewable application manifests.
- Pin chart versions before promoting changes.
- Make rollback possible from Git history.
- Document every cluster-specific assumption in `docs/`.

## Status

This repository is being built as a public GitOps reference for a Kubernetes observability stack. The next useful milestones are adding Argo CD `Application` manifests, a Grafana ingress, and a short recovery runbook.
