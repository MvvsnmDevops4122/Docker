
# 🚀 Docker ECR (Elastic Container Registry) Setup Guide
============================================================

## ✅ What is Docker ECR (Amazon Elastic Container Registry)?

- **Amazon ECR** is a fully managed Docker container registry provided by **AWS**.
- It works like a **private DockerHub** to store your Docker images.
- Securely stores Docker images with **encryption**.
- Helps you easily **store, manage, and deploy** Docker container images.


## ✅ 1. Install AWS CLI v2 on Ubuntu
======================================

### 🔹 Step 1: Update system packages & install unzip

sudo apt update
sudo apt install unzip curl -y

### 🔹 Step 2: Download the AWS CLI v2 installer

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

### 🔹 Step 3: Unzip the installer

unzip awscliv2.zip

### 🔹 Step 4: Run the installation script

sudo ./aws/install

### 🔹 Step 5: Verify the installation

aws --version

## ✅ 2. Configure AWS CLI (Authentication with Docker to AWS)
===============================================================

> 📌 Get your **Access Key ID** and **Secret Access Key** from:

> AWS Console → IAM → Your user → Security credentials → Create access key

### 🔹 Run the configure command:

aws configure

### Example:

AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: ap-south-1
Default output format [None]: json

You can test with: aws s3 ls

## ✅ 3. Create an ECR Repository
==================================

1. Go to **AWS Console**
2. Search for **ECR**
3. Click on **Repositories → Create Repository**
4. Provide a custom **repository name** (e.g., `satya`)
5. Click **Create**

## ✅ 4. Push Docker Image to ECR
=====================================

> ℹ️ AWS Console gives you all these commands, but here’s the breakdown:

### 🔹 Step 1: Authenticate Docker to ECR

aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 920373019152.dkr.ecr.ap-south-1.amazonaws.com

### 🔹 Step 2: Tag the Image

docker tag springimage 920373019152.dkr.ecr.ap-south-1.amazonaws.com/satya:latest

 ✅ Make sure `springimage` exists locally:

docker images

### 🔹 Step 3: Push the Image to ECR

docker push 920373019152.dkr.ecr.ap-south-1.amazonaws.com/satya:latest

### 🔹 Step 4: (Optional) Pull the Image from ECR

docker pull 920373019152.dkr.ecr.ap-south-1.amazonaws.com/satya:latest


✅ **Done!** Your Docker image is now pushed to AWS ECR and ready for use in ECS, Kubernetes, or any other containerized deployment.
