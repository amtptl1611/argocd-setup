# argocd-setup

Instructions to setup argocd on local minikube cluster.

# Pre-requisite
1. Kubernetes Up using minikube
2. Kubectl and argocd install on local machine

# Setup Argo CD 

## Install Argo CD
kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

## Access The Argo CD API Server

By default, the Argo CD API server is not exposed with an external IP. To access the API server, choose one of the following techniques to expose the Argo CD API server:

### Port Forwarding:
Kubectl port-forwarding can also be used to connect to the API server without exposing the service.

kubectl port-forward svc/argocd-server -n argocd 8000

The API server can then be accessed using https://localhost:8000

## Login Using The CLI
Get password using below command

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

### Login via CLI
argocd login <ARGOCD_SERVER>

### Change password
argocd account update-password

----------------------------------------------------------------------------------
# Run Sample Applications steps





## References - 
https://argo-cd.readthedocs.io/en/stable/getting_started/ 
