trapi Deployment using GitHub Actions and Terraform

Project Overview

This project automates the deployment of a Strapi application using Docker, GitHub Actions, and Terraform.

The system automatically builds and pushes a Docker image when code is pushed to the main branch.
Terraform is then triggered manually to deploy the updated image on an AWS EC2 instance.

Architecture

Developer pushes code to GitHub
GitHub Actions builds Docker image
Docker image is pushed to Docker Hub
Terraform provisions EC2 instance
EC2 installs Docker and runs Strapi container
Strapi is accessible using EC2 Public IP on port 1337

Technologies Used

Strapi
Docker
GitHub Actions
Terraform
AWS EC2
Docker Hub

Project Structure

strapi-cicd-terraform
.github
workflows
ci.yml
terraform.yml
terraform
main.tf
provider.tf
variables.tf
outputs.tf
Dockerfile
.dockerignore
package.json
README.md

Prerequisites

Install these tools on your local machine:

Git
Node.js version 18 or above
Docker Desktop
Terraform
AWS Account
Docker Hub Account

GitHub Secrets Required

Add the following secrets in GitHub repository settings:

AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_REGION
DOCKER_USERNAME
DOCKER_PASSWORD

How It Works

CI Pipeline

Triggered automatically on push to main branch
Builds Docker image of Strapi
Tags the image
Pushes the image to Docker Hub

CD Pipeline

Triggered manually using workflow dispatch
Runs terraform init
Runs terraform plan
Runs terraform apply
Creates EC2 instance with 15GB root volume
Configures 2GB swap memory
Installs Docker
Pulls latest Docker image
Runs Strapi container

Deployment Steps

Step 1
Clone repository

git clone repository_url

Step 2
Create Strapi project

npx create-strapi-app my-strapi

Step 3
Add Dockerfile

Step 4
Push project to GitHub

Step 5
Push code to main branch

This triggers CI workflow

Step 6
Go to GitHub Actions
Manually trigger Terraform workflow

Step 7
After successful apply
Check Terraform output

You will get public_ip

Access application using

http://public_ip:1337

Storage Configuration

Root volume size is 15GB
2GB swap memory configured during EC2 startup

Verification

After deployment

Open browser
Enter EC2 public IP with port 1337

If everything is correct
Strapi admin panel will load

Common Issues

Security group already exists
Rename security group or delete existing one

Terraform reference error
Ensure resource names match exactly

Docker login failure
Check Docker Hub credentials in GitHub secrets

Conclusion

This project demonstrates full CI CD automation using Docker, GitHub Actions, Terraform, and AWS.

Code push triggers Docker image build.
Manual workflow triggers infrastructure provisioning.
Application is deployed automatically on EC2.

You now have a complete DevOps pipeline for Strapi deployment.
