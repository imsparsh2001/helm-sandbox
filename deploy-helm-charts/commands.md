helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm install helm-nginx bitnami/nginx
helm list
kubectl get pods

<!-- To see available values for customization, run: -->
helm show values bitnami/nginx
<!-- To preview the manifest without deploying: -->
helm template my-nginx bitnami/nginx

<!-- Upgrading NGINX using Helm -->
helm upgrade my-nginx bitnami/nginx --set service.type=NodePort
helm status my-nginx


helm uninstall helm-nginx
helm search repo bitnami | grep nginx 