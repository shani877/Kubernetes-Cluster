Installing Kubernetes Dashboard

Deploy Kubernetes dashboard:
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml

Apply yaml for creating service and and user
kubectl apply dashboard-adminuser.yaml

kubectl get svc -n kubernetes-dashboard
kubectl port-forward svc/kubernetes-dashboard -n kubernetes-dashboard 8080:443 --address=0.0.0.0 &

Create a token for dashboard access:
kubectl -n kubernetes-dashboard create token admin-user # Use this token at access time


Access dashboard
https://IP:8080
