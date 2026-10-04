# ArgoCD
kubectl create namespace argocd
kubectl get namespace argocd
kubectl apply -n argocd --server-side --force-conflicts -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl get pods -n argocd
      NAME                                      READY   STATUS
      argocd-application-controller-xxx         1/1     Running
      argocd-applicationset-controller-xxx      1/1     Running
      argocd-dex-server-xxx                     1/1     Running
      argocd-notifications-controller-xxx       1/1     Running
      argocd-redis-xxx                          1/1     Running
      argocd-repo-server-xxx                    1/1     Running
      argocd-server-xxx                         1/1     Running
kubectl get svc -n argocd
      NAME                    TYPE        CLUSTER-IP
      argocd-server           ClusterIP   xxx
      argocd-repo-server      ClusterIP   xxx
      argocd-redis            ClusterIP   xxx
      
kubectl port-forward svc/argocd-server -n argocd 2222:443  # Port forward   
https://localhost:2222 # access locally from browser
argocd admin initial-password -n argocd #Username=admin, get password from below command
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d #Copy password from this command
      
