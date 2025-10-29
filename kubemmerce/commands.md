helm create kubemmerce

helm install kubemmerce ./kubemmerce
helm list
kubectl get svc
kubectl port-forward svc/myapp 8080:80
