mkdir -p helm-repo/{payments,shipping}
cd helm-repo

helm create payments
helm create shipping

helm package payments
helm package shipping
helm repo index .

git init
git remote add origin https://github.com/username/helm-repo.git

git add .
git commit -m "Add payments and shipping charts"
git push -u origin main


helm repo add myrepo https://username.github.io/helm-repo
helm repo update
helm search repo myrepo
helm install payments-service myrepo/payments