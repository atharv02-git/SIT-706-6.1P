# SIT706-6.1P - Phase 1 AWS Infrastructure Deployment

This repository contains the CloudFormation templates used to automate the deployment of a highly available WordPress application on AWS, as part of **SIT706-6.1P** final project.

---

## 📁 Files Included

- `phase1-network.yaml`  
  Provisions the complete networking layer including:
  - Custom VPC with CIDR block `192.168.0.0/16`
  - Two Public and Two Private Subnets
  - Internet Gateway and NAT Gateway
  - Route Tables and Associations

- `phase1a-application.yaml`  
  Deploys the core application infrastructure:
  - MySQL RDS (Multi-AZ) with a Read Replica
  - Application Load Balancer (ALB)
  - Security Groups
  - EC2 instance with WordPress pre-installed
  - S3 bucket for media offload

- `phase1b-autoscaling.yaml`  
  Implements auto-scaling for the WordPress application:
  - Launch Configuration using a custom AMI
  - Auto Scaling Group with min=1, max=3
  - CloudWatch alarms to trigger scaling policies (CPU > 70% or < 25%)

---

## 🚀 Deployment Steps (Manual via Console)

1. Go to **AWS CloudFormation > Create stack**.
2. Choose **"With new resources (standard)"**.
3. Select **"Upload a template file"** and upload `phase1-network.yaml`.
4. After the network stack is deployed successfully, repeat the above steps for `phase1a-application.yaml`, then `phase1b-autoscaling.yaml`.
5. Ensure the parameter inputs (like stack names, AMI ID, etc.) are correctly passed when prompted.

---
