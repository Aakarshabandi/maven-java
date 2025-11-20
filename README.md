# maven-java
for miniqube 
:: Start Minikube with Docker driver
minikube start --driver=docker

:: Check Minikube status
minikube status

:: Check Kubernetes node readiness
kubectl get nodes

:: Create Nginx deployment
kubectl create deployment mynginx --image=nginx

:: Verify pod is created
kubectl get pods

:: Expose deployment using NodePort
kubectl expose deployment mynginx --type=NodePort --port=80

:: Verify service
kubectl get svc

:: Scale deployment to 4 replicas
kubectl scale deployment mynginx --replicas=4

:: Verify pods after scaling
kubectl get pods -o wide

:: Open the service in browser (Auto Opens URL)
minikube service mynginx --url
(or)
kubectl port-forward svc/mynginx 8081:80
(or)
http://localhost:8081


:: Open Kubernetes dashboard
minikube dashboard
