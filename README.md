# demo-kube

Démo GitOps sur un cluster Kubernetes Hikube avec Argo CD.

| Chemin | Rôle |
|---|---|
| `platform/argocd/` | Installation Argo CD v3.5.8 (kustomize), mode `server.insecure` derrière NGINX Ingress, Ingress TLS |
| `platform/cluster-issuer.yaml` | ClusterIssuer Let's Encrypt (HTTP-01 via IngressClass `nginx`) |
| `platform/application-demo-web.yaml` | Application Argo CD qui suit `apps/demo-web` en sync **manuel** (OutOfSync après push, clic SYNC pour appliquer) |
| `apps/demo-web/` | Appli PHP de démo (php:8.4-apache, 2 réplicas) : affiche la version PHP, le pod et une couleur de fond |

URL :
- Argo CD : https://argocd.91-223-132-198.sslip.io
- Appli : https://demo.91-223-132-198.sslip.io

Démo : changer `BG_COLOR` (et `APP_VERSION`) dans `apps/demo-web/deployment.yaml`, pousser sur `main` ; Argo CD détecte le commit (polling 3 min, ou bouton Refresh) et passe OutOfSync ; cliquer SYNC applique le changement (rolling update des pods).

Aucun identifiant n'est stocké dans ce dépôt.
