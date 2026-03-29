#  AWS ECR Docker Demo

## Project Overview

This project demonstrates how to:

* Create a private container repository in AWS ECR
* Authenticate Docker with AWS
* Build a Docker image
* Push the image to a private AWS ECR repository

---

## Technologies Used

* AWS (ECR)
* Docker
* AWS CLI

---

## Prerequisites

Make sure you have installed and configured:

* AWS CLI (`aws configure`)
* Docker Desktop
* AWS account with ECR access

---

## Step 1: Create ECR Repository

Create a repository in AWS:

```bash
aws ecr create-repository --repository-name my-app --region eu-central-1
```

---

## step 2: Authenticate Docker with AWS

```bash
aws ecr get-login-password --region eu-central-1 | docker login --username AWS --password-stdin <your-repo-url>
```

---

## Step 3: Build Docker Image

```bash
docker build -t my-app .
```

---

## Step 4: Tag Image

```bash
docker tag my-app:latest <your-repo-url>:latest
```

---

## Step 5: Push Image to ECR

```bash
docker push <your-repo-url>:latest
```

---

## Result

Your Docker image is now stored securely in AWS ECR and can be pulled from anywhere with proper authentication.

---

## What I Learned

* How to use AWS ECR as a private Docker registry
* Authenticating Docker with AWS CLI
* Managing container images in the cloud

---

Notes

* Make sure AWS credentials are configured
* Free tier limits apply (ECR storage)

---

## Cleanup

To avoid costs:

```bash
aws ecr delete-repository --repository-name my-app --force --region eu-central-1
```

---

## Author

Created as part of a DevOps Bootcamp project.
