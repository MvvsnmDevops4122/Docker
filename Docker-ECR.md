
====================================================================================================================

                                 DOCKER-ECR(Elastic container Registry)

=====================================================================================================================

## What is Docker ECR (Amazon Elastic Container Registry)?
----------------------------------------------------------

* Docker ECR (Amazon Elastic Container Registry) is a fully managed Docker container registry service provided by AWS.

* Acts like a private DockerHub for your docker images.

* Securely stores Docker images with encryption.

* Allowing developers to store, manage, and deploy Docker container images easily and securely.



1.✅ How to Install AWS CLI v2 on Ubuntu
-----------------------------------------

🔹 Step 1: Update system packages & install unzip
-------------------------------------------------

sudo apt update
sudo apt install unzip curl -y


🔹 Step 2: Download the AWS CLI v2 installer
--------------------------------------------

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"


🔹 Step 3: Unzip the installer
------------------------------

unzip awscliv2.zip


🔹 Step 4: Run the installation script
--------------------------------------

sudo ./aws/install


🔹 Step 5: Verify the installation
----------------------------------

aws --version


2.✅ How to Configure AWS CLI on Ubuntu (Authentication with docker server to aws)
======================================

AWS console ---> Profile ----> security credentials ---> create access key.


After installing the CLI, run: aws configure

🔹 1. AWS Access Key ID: Enter your Access Key ID from your AWS IAM user.
-----------------------


🔹 2. AWS Secret Access Key: Enter the Secret Access Key associated with your Access Key ID.
---------------------------


🔹 3. Default Region Name:
--------------------------

Example: us-east-1 (Or use your preferred region like ap-south-1 (Mumbai), etc.)

📝 Example

aws configure
AWS Access Key ID [None]: Enter access key id
AWS Secret Access Key [None]: Enter secret access key pwd
Default region name [None]: region
Default output format [None]: json

Once configured, you can test it with: aws s3 ls



3.✅  Create an ECR Repository
===============================

🔹 1. Login to AWS Console :  Go to the AWS Console.
--------------------------


🔹 2. Search for "ECR" : In the search bar, type ECR and open Elastic Container Registry.
------------------------


🔹 3. Click "Create Repository: On the left menu, click on Repositories → then click Create repository.
-------------------------------


🔹 4. Provide a Repository Name: Custome name
-------------------------------

🔹 5. Click "Create"
-------------------

4. ✅ Push Docker Image to ECR
================================

(No need to remaind below commands AWS provide us all in console)

🔹 1. Authenticate Docker to ECR:

aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 920373019152.dkr.ecr.ap-south-1.amazonaws.com


🔹 2. Tag the Image: docker tag springimage 123456789012.dkr.ecr.ap-south-1.amazonaws.com/satya:latest (Already have springimage my local)


🔹 3. Push the Image to ECR:  docker push 920373019152.dkr.ecr.ap-south-1.amazonaws.com/satya:latest

🔹 4. Pull the Image to ECR:  docker pull 920373019152.dkr.ecr.ap-south-1.amazonaws.com/satya:latest



                       
