1. Install argocd
    ```
    helm install argocd argo/argo-cd \
        --namespace argocd \
        --create-namespace \
        --set server.extraArgs={--insecure} \
        --set server.config."users\.anonymous\.enabled"="true"
    ```

1. Install argo events
    ```
    helm install argo-events argo/argo-events \
    --namespace argo-events \
    --create-namespace
    ```

1. Install argo workflows
    ```
    helm repo add argo https://argoproj.github.io/argo-helm

    helm install argo-workflows argo/argo-workflows \
    -n argo-workflows \
    --create-namespace \
    -f values.yaml
    ```

1. Install rollotus (to use analysis templates)
    ```
    helm install argo-rollouts argo/argo-rollouts \
    --namespace argo-rollouts \
    --create-namespace \
    --set installCRDs=true
    ```

1. Access argo workflows UI
    ```
    kubectl -n argo-workflows port-forward service/argo-workflows-server 2746:2746
    ```

1. Access argocd UI
    ```
    kubectl port-forward -n argocd svc/argocd-server 80:8080
    ```

1. Go to github and create a PAT to connect argocd

1. Add a new repository in argocd ui

1. Deploy the argocd apps
    ```
    kubectl apply -f argo/apps.yaml
    ```

1. To test the workflow, update the image in helm/app-database/values.yaml and push to github

## Example workflow

![alt text](<Screenshot 2025-04-17 at 2.03.12 AM.png>)

![alt text](<Screenshot 2025-04-17 at 2.04.10 AM.png>)


