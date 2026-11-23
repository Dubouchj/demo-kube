# demo-kube

Démo GitOps sur un cluster Kubernetes Hikube avec Argo CD.

| Chemin | Rôle |
|---|---|
| `platform/argocd/` | Installation Argo CD v3.5.8 (kustomize), mode `server.insecure` derrière NGINX Ingress, Ingress TLS |
| `platform/cluster-issuer.yaml` | ClusterIssuer Let's Encrypt (HTTP-01 via IngressClass `nginx`) |
| `platform/application-demo-web.yaml` | Application Argo CD qui synchronise `apps/demo-web` (auto-sync, prune, self-heal) |
| `apps/demo-web/` | Appli de démo nginx (2 réplicas) exposée en HTTPS |

URL :
- Argo CD : https://argocd.91-223-132-198.sslip.io
- Appli : https://demo.91-223-132-198.sslip.io

Démo : modifier `apps/demo-web/configmap.yaml` (texte) ou `replicas` dans `deployment.yaml`, pousser sur `main`, Argo CD détecte et déploie (polling 3 min, ou bouton Refresh).

Aucun identifiant n'est stocké dans ce dépôt.
