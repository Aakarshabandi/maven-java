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
do this in normal command prompt run as powershell





aws
first do all things in aws larning lab and moe to powershell run as administrator
# -----------------------------
# 1. Go to the folder with your key file
# -----------------------------
cd C:\Users\<yourusername>\Downloads


# -----------------------------
# 2. Connect to EC2 using SSH
# (Replace the DNS with your instance's SSH command)
# -----------------------------
ssh -i "awskey.pem" ubuntu@ec2-XX-XX-XXX-XXX.compute.amazonaws.com


# -----------------------------
# 3. Update and upgrade packages
# -----------------------------
sudo apt update
sudo apt upgrade -y


# -----------------------------
# (If reboot needed)
# -----------------------------
sudo reboot

# (Reconnect using SSH again)
ssh -i "awskey.pem" ubuntu@ec2-XX-XX-XXX-XXX.compute.amazonaws.com


# -----------------------------
# 4. Install Docker, Git, Nano
# -----------------------------
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

sudo apt install git -y
sudo apt install nano -y


# -----------------------------
# 5. Create project folder
# -----------------------------
mkdir mywebapp
cd mywebapp


# -----------------------------
# 6. Create index.html
# -----------------------------
nano index.html

# (Paste this inside nano)
# --------------------------------
# <!DOCTYPE html>
# <html>
# <head>
#     <title>My AWS Web App</title>
# </head>
# <body>
#     <h1>Welcome to my EC2 + Docker Deployment!</h1>
#     <p>Deployed by: Vindhya</p>
# </body>
# </html>
# --------------------------------

# (Save: CTRL + O, Enter, CTRL + X)


# -----------------------------
# 7. Create Dockerfile
# -----------------------------
nano Dockerfile

# (Paste this inside nano)
# --------------------------------
# FROM nginx:alpine
# COPY index.html /usr/share/nginx/html/index.html
# --------------------------------

# (Save same as above)


# -----------------------------
# 8. Build Docker image
# -----------------------------
sudo docker build -t mywebimage .


# -----------------------------
# 9. Run Docker container
# -----------------------------
sudo docker run -d -p 80:80 mywebimage


# -----------------------------
# 10. Check running containers
# -----------------------------
sudo docker ps


# -----------------------------
# 11. Stop & remove container (if needed)
# -----------------------------
sudo docker stop <container-id>
sudo docker rm <container-id>


# -----------------------------
# 12. Run again after update (optional)
# -----------------------------
sudo docker build -t mywebimage .
sudo docker run -d -p 80:80 mywebimage
sudo docker ps

