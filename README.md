kubectl apply -f k8s/configmap.yaml
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml

kubectl get nodes -o wide

curl http://172.19.0.2:30080 // INTERNAL IP

kubectl port-forward svc/test-app-service 8080:80
curl http://localhost:8080 // FORWARDED PORT
