@@@@@@@@scriptedpipeline

pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'
    }

    stages {

        stage('Clone Repo & Clean') {
            steps {
                bat 'IF EXIST mv-javaproj rmdir /s /q mv-javaproj'
                bat 'git clone https://github.com/AdepuTriveni/mv-javaproj.git'
                bat 'mvn clean -f mv-javaproj/pom.xml'
            }
        }

        stage('Install') {
            steps {
                bat 'mvn install -f mv-javaproj/pom.xml'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test -f mv-javaproj/pom.xml'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package -f mv-javaproj/pom.xml'
            }
        }
    }
}
another code

pipeline {
    agent any

    tools {
        maven 'MAVEN-HOME'
    }

    stages {
        stage('git repo & clean') {
            steps {
                bat 'git clone https://github.com/GirijaSundari/Maven.git'
                bat 'mvn clean -f Maven/pom.xml'
            }
        }

        stage('install') {
            steps {
                bat 'mvn install -f Maven/pom.xml'
            }
        }

        stage('test') {
            steps {
                bat 'mvn test -f Maven/pom.xml'
            }
        }

        stage('package') {
            steps {
                bat 'mvn package -f Maven/pom.xml'
            }
        }
    }
}

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

################3

1. Go to AWS Academy Learner Lab → Start Lab → AWS

2. Open EC2 service.

3. Click "Launch Instance".

4. Set the following:
   - Name: MyWebServer
   - OS Image: Ubuntu Server 22.04 (Free tier eligible)
   - Instance Type: t3.micro

5. Create Key Pair:
   - Name: awskey
   - Type: RSA
   - Format: .pem

6. Network Settings:
   ✔️ Allow SSH (Port 22)
   ✔️ Allow HTTP (Port 80)
   ✔️ Allow HTTPS (Port 443)

7. Storage:
   - Keep default 8 GiB gp3

8. Click "Launch Instance".

9. Go to:
   EC2 Dashboard → Instances → Instances1. Select your instance.
2. Click "Connect".
3. Go to the "SSH Client" tab.
4. Copy the SSH command provided by AWS.
   It looks like this:

   ssh -i "awskey.pem" ubuntu@ec2-xx-xxx-xxx-xxx.compute.amazonaws.com

5. Open PowerShell on your computer.
6. Go to the folder where your key file is saved:

   cd C:\Users\<yourusername>\Downloads

7. Paste the SSH command you copied from AWS and press Enter.

8. If asked "Are you sure you want to continue connecting?", type:
   yes




@@@@webhooks

# --------------------------------------------
# STEP-0 (Ensure Before Starting)
# --------------------------------------------
# ✔ Jenkins running on: http://localhost:8080  (or 8085)
# ✔ Your GitHub repo already exists
# ✔ Maven installed, Git installed
# --------------------------------------------


# --------------------------------------------
# STEP-1 — Start ngrok Tunnel for Jenkins
# --------------------------------------------
# Open PowerShell in ngrok folder:
cd "C:\Users\USER\Downloads\ngrok-v3-stable-windows-amd64"

# If Jenkins is on 8080:
.\ngrok.exe http 8080
# If Jenkins is on 8085:
# .\ngrok.exe http 8085

# COPY the HTTPS Forwarding URL from output (example)
# https://abcd1234.ngrok-free.app
# KEEP NGROK WINDOW OPEN


# --------------------------------------------
# STEP-2 — Add GitHub Webhook
# --------------------------------------------
# Go to GitHub repository → Settings → Webhooks → Add Webhook
# Fill like below:
# Payload URL:
# https://YOUR_NGROK_URL/github-webhook/
#
# Example:
# https://abcd1234.ngrok-free.app/github-webhook/
#
# Content type → application/json
# Trigger → Just the push event
# Click: Add Webhook


# --------------------------------------------
# STEP-3 — Configure Jenkins Job
# --------------------------------------------
# Jenkins → Select Your Job → Configure

# Source Code Management:
# Select: Git
# Paste your repo URL:
# https://github.com/<username>/<repo>.git

# Build Triggers:
# ✔ GitHub hook trigger for GITScm polling

# Build:
# Add build step → Invoke top-level Maven targets
# Goals:
clean install

# Click: Save


# --------------------------------------------
# STEP-4 — Test Webhook
# --------------------------------------------
# Make a small code change and push:
git add .
git commit -m "Webhook Test Build"
git push

# --------------------------------------------
# RESULT (Expected):
# 🚀 Jenkins automatically starts a new build!
# No need to press “Build Now”
# --------------------------------------------

