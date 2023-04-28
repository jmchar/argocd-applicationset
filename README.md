# argocd-applicationset

Implementing the ArgoCD ApplicationSet using Git Files generator.


## Setting up ArgoCD on Minikube
### Download Tools
```
brew install minikube
brew install argocd
brew install kubectl
```

### Install Argo CD
```
minikube start
kubectl create ns argocd
kubectl get ns
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl get all -n argocd
kubectl get svc -n argocd
```

### Access The Argo CD API Server
```
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
kubectl port-forward svc/argocd-server -n argocd 8080:443

```

### ArgoCD Login and Change admin Password
```
argocd admin initial-password -n argocd
argocd login localhost:8080 --grpc-web-root-path /argo-cd
argocd account update-password

```

### ArgoCD UI
```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

http://localhost:8080
username: admin
password: {}

## Create ApplicationSet
```
kubectl apply -f applicationset.yaml -n argocd
```
or
```
kubectl config set-context --current --namespace=argocd
argocd appset create applicationset.yaml
```