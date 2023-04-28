# argocd-applicationset

Implementing the ArgoCD ApplicationSet using Git Files generator.


## Setting up ArgoCD on local machine
- brew install minikube
- brew install argocd
- brew install kubectl

- minikube start
- kubectl create namespace argocd
- kubectl get ns
- kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
- kubectl get all -n argocd

- kubectl port-forward svc/argocd-server -n argocd 8080:443
- http://localhost:8080
- username: admin
- password: {argocd admin initial-password}


## Create ApplicationSet
- kubectl apply -f applicationset.yaml -n argocd
- argocd appset create applicationset.yaml