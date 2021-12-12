# gitops_sample

This is a repository for learning and study purpose.


## 1. Install requirements

* helm
* argocd
* minikube

## 2. Install argocd via helm

```
    helm install argo-cd argo/argo-cd --version 3.28.1 -n argocd -f argo-cd/install/helm/values.yaml --create-namespace
```

### 3. Create projects

```
    kubectl apply -f argo-cd/projects
```

### 4. Create applications (hello + prometheus operator)

```
    kubectl apply -f argo-cd/applications
```

## 5. Enable argo-cd servicemonitor (chicken egg issue)

```
    helm upgrade argo-cd argo/argo-cd --version 3.28.1 -n argocd -f argo-cd/install/helm/values-servicemonitor.yaml --create-namespace
```


### 5. login to argocd console

```
    kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
    minikube service list
```

