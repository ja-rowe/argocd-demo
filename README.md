# GitOps for K8s with Argo CD


> This repo contains the K8s manifests used in a demo of Argo CD.

## Setup
1. Deploy Argo CD to your cluster using this [Helm Chart](https://artifacthub.io/packages/helm/argo/argo-cd) like so:
```sh
helm repo add argo https://argoproj.github.io/argo-helm

helm repo update

helm install my-argo-cd argo/argo-cd --version 6.7.12 --set "server.service.type=NodePort"
```
2. Retrieve the password for Argo CD using the following command:
```sh
kubectl -n default get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```
3. Login with username: `admin` and the password you retrieved in step 2.
4. Follow the instructions seen here in the [Argo CD docs](https://argo-cd.readthedocs.io/en/stable/getting_started/#creating-apps-via-ui) to create and deploy the application.
5. It should be accessible at http://server-ip:30081
