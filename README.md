Install argocd
    ```
    helm install argocd argo/argo-cd \
        --namespace argocd \
        --create-namespace \
        --set server.extraArgs={--insecure} \
        --set server.config."users\.anonymous\.enabled"="true"
    ```

Install argo events
    ```
    helm install argo-events argo/argo-events \
    --namespace argo-events \
    --create-namespace
    ```

Install argo workflows
    ```
    helm repo add argo https://argoproj.github.io/argo-helm

    helm install argo-workflows  argo/argo-workflows -n argo-workflows --create-namespace
    ```

Install rollotus (to use analysis templates)
    ```
    helm install argo-rollouts argo/argo-rollouts \
    --namespace argo-rollouts \
    --create-namespace \
    --set installCRDs=true
    ```

## Example workflow

![alt text](<Screenshot 2025-04-17 at 2.03.12 AM.png>)

![alt text](<Screenshot 2025-04-17 at 2.04.10 AM.png>)
