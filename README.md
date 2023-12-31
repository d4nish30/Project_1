# Deploying Django Web App on AWS EC2 via Terraform and Docker
This repository contains Terraform files, Dockerfile, and a Django web application for deploying a Django-based web application
on an AWS EC2 instance using Terraform and Docker.
## Project Overview:

## Creates an EC2 instance on AWS using Terraform File (main.tf)
- Creates an EC2 instance on AWS.
- Generates a key pair.
- Defines a VPC, subnet, and routable configurations.
- Sets up security groups for necessary access.

```sh
#  To generate key-pair
ssh-keygen -t ras
```
Initialize a working directory containing terraform configuration files.
```sh
#  To Initialize
terraform init
```

To create an execution plan and examine your terraform configuration and compares it to the current state of the infrastructure defined in your files and save it in a file named 'Plan' in the current directory.
```sh
# To create and execute
terraform plan --out=plan
```
To apply the changes defined in your Terraform configuration files to the infrastructure, It executes the changes that were palnned.
```sh
# To apply the changes
terraform apply
```
Now you have successfully created your ec2-instance on AWS using terraform and also you get your public ip now access to ec2 instance from cli
To connect to an EC2 instance using a generated private key

```sh
# Connect to ec2-instance
ssh -i ~/.ssh/id_rsa ec2user@publicip

# change your publicip with yours
```
Download and install github and docker in your ec2-instance

```sh
# git install and verify
sudo yum install git
git --version

# docker
sudo yum install docker
docker --version
```

To start docker and check running status

 ```sh
# start 
sudo systemctl start docker

# check status
sudo systemctl status docker
```
Now you have to clone my repository to deply web-app
To clone my repository you have to use command 
```sh
# Clone
git clone https://github.com/d4nish30/Project_1.git

```
Now cd to Project_1 directory and build a docker image with dockerfile you have already a dockerfile in Project_1 directory
```sh
# build docker image
docker build -t example .
# change tagname example as you wish 

```
To see the iamges in your local 
```sh
docker images
```

Now image is build, you have to just run a image so that you can access container.
```sh
# run docker image
docker run -p 3000:8000 -it --name django example

# you can change your port as your wish
```
Now everything is all setup, you have to just access your web-app on browser
```sh
# run docker image
http://your-ec2-instance-public-ip:3000
```
You got a screen like this
![image](https://github.com/d4nish30/Project_1/assets/130281960/f3b04b6c-550e-4c05-ad8f-095171f5b889)

Congratulation you have successfully deploy a Django Web App


Ensure security configurations are appropriately set in your AWS account to avoid any vulnerabilities.
Make sure to keep your AWS credentials secure.
Modify configurations in Terraform files according to your requirements.
For detailed information on each file and the deployment process, refer to the individual files in this repository.

