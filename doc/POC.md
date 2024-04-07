# k3d ArgoCD deployment & access

Create a cluster and namespace:

```bash
k3d cluster create argo

kubectl cluster-info

kubectl create namespace argocd
```

Apply ArgoCD manifest and wait while all services started

```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl get pod -n argocd -w
```

Forward listening port and get admin password

```bash
kubectl port-forward svc/argocd-server -n argocd 8081:443&

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"|base64 -d;echo
```

[CLI demo](https://asciinema.org/a/AeCEtyx1g6qNFwD5j05XJNEfO):
![Image](.data/ArgoCD_install_demo.gif)

Web GUI demo:
![Image](.data/ArgoCD_WEB_GUI_demo.gif)

CLI install

```bash
curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd
rm argocd-linux-amd64
```

CLI login

```bash
argocd login 127.0.0.1:8081
Username: admin
Password: 
# 'admin:login' logged in successfully
# Context '127.0.0.1:8081' updated
```

Add local user:

```bash
kubectl get configmap argocd-cm -n argocd -o yaml > argocd-cm.yml
nano argocd-cm.yml
# add 2 lines
# data:
#  accounts.username: apiKey, login
kubectl apply -f argocd-cm.yml
# configmap/argocd-cm configured
argocd account update-password --account username
# *** Enter password of currently logged in user (admin): 
# *** Enter new password for user username: 
# *** Confirm new password for user username: 
# Password updated
```
