# tal_devops_assignment_react
## Application 1: Task Management System (React.js + Node.js)

### Overview
A full-stack task management application built with React.js frontend and Node.js backend, featuring task creation, management, and status tracking.

## Project Structure
```
.
├── frontend/         # React.js frontend application
├── backend/         # Node.js backend application
└── k8s/            # Kubernetes configuration files
```

## Prerequisites
- Node.js 18.x or later
- Docker
- kubectl
- AWS CLI
- eksctl
- AWS 

## Steps to deploy
Terraform is used for creation of EKS cluster and state of cluster is stored in S3 bucket with DynamoDB for state locking. For storing images, Amazon ECR have been used. The application is configured to be deployed on Amazon EKS. The application uses Amazon RDS (PostgreSQL) as the database. Connection details have been configured through environment variables. 

### Infrastructure Creation
- Create DynamoDB and S3 bucket for storing Terraform state and state locking. The code for creation of S3 bucket and DynamoDB is at 'state-lock-terraform' 
- Create EKS cluster using TF code present at 'terraform-eks-cluster'. 
- Create AWS RDS DB instance using AWS console. Edit inbound rule of AWS RDS DB to allow incoming traffic from EKS cluster at port 5432.
- Create frontend and backend repositories in AWS ECR.
- Build docker images for frontend and backend and push docker images to the ECR repositories.

### Deployment
- Deployment files are present at k8s 
- Run kubectl apply commands and deploy all the three yaml files, secrets.yaml, node-deployment.yaml and react-deployment.yaml
