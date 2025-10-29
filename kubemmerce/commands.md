helm create kubemmerce

helm install kubemmerce ./kubemmerce
helm list
kubectl get svc
kubectl port-forward svc/kubemmerce 8080:80

helm upgrade kubemmerce ./kubemmerce 

helm uninstall kubemmerce
