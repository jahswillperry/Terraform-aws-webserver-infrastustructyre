
# Terraform AWS Webserver Infrastructure

## Project Description

This project aims to demonstrate the deployment and management of a web server infrastructure on AWS using Terraform as Infrastructure as Code (IaC). It automates the creation of various AWS resources, such as Virtual Private Cloud (VPC), S3 buckets, IAM roles, Auto Scaling Group (ASG), Application Load Balancer (ALB), CloudWatch alarms, and more. The infrastructure hosts a web server with a customized web page.

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Project Structure](#project-structure)
4. [Deployment Steps](#deployment-steps)
   - [Step 1: Terraform Backend for State Storage](#step-1-terraform-backend-for-state-storage)
   - [Step 2: IAM Role and Launch Configuration](#step-2-iam-role-and-launch-configuration)
   - [Step 3: Auto Scaling Group and Load Balancer](#step-3-auto-scaling-group-and-load-balancer)
   - [Step 4: CloudWatch Alarms and Scaling Policies](#step-4-cloudwatch-alarms-and-scaling-policies)
5. [Usage and Testing](#usage-and-testing)
6. [Conclusion](#conclusion)

## Introduction

The primary goal of this project is to showcase the power of Infrastructure as Code (IaC) by utilizing Terraform to automate the provisioning and configuration of a scalable and highly available web server infrastructure on AWS. The infrastructure includes a custom web page and demonstrates best practices in security, monitoring, and scaling.

## Prerequisites

- An AWS account with appropriate IAM user credentials and access keys.
- Terraform installed on your local machine.
- Basic knowledge of AWS services and Terraform.

## Project Structure

The project is organized into separate directories for each set of resources:

- **01-terraform-backend**: Configures S3 backend for Terraform state storage and state locking.
- **02-iam-lc-asg**: Sets up IAM role, launch configuration, and Auto Scaling Group.
- **03-asg-lb**: Creates Auto Scaling Group, Application Load Balancer, and target group.
- **04-cloudwatch-alarms**: Defines CloudWatch alarms and scaling policies.

## Deployment Steps

Follow these steps to deploy the web server infrastructure:

### Step 1: Terraform Backend for State Storage

This step sets up the S3 backend for storing the Terraform state file and uses DynamoDB for state locking support.

### Step 2: IAM Role and Launch Configuration

Creates an IAM role with permissions to access S3 bucket and AWS Systems Manager (Session Manager). Configures the launch configuration with user data script to pull index.html from S3 and attach the IAM role.

### Step 3: Auto Scaling Group and Load Balancer

Sets up the Auto Scaling Group in the private subnet, along with a target group and Application Load Balancer in the public subnet.

### Step 4: CloudWatch Alarms and Scaling Policies

Defines CloudWatch alarms to send notifications when ASG state changes and scaling policies to scale out/in based on CPU utilization.

## Usage and Testing

1. Clone the repository to your local machine:

```bash
git clone https://github.com/jahswillperry/terraform-aws-webserver-infrastructyre.git
```

2. Update the necessary placeholder values in the Terraform configuration files (region, bucket names, IAM role name, etc.).

3. Run Terraform commands in each directory to deploy the infrastructure:

```bash
cd 01-terraform-backend
terraform init
terraform apply

cd ../02-iam-lc-asg
terraform init
terraform apply

cd ../03-asg-lb
terraform init
terraform apply

cd ../04-cloudwatch-alarms
terraform init
terraform apply
```

4. After deploying, verify the infrastructure on AWS console.

## Conclusion

In conclusion, this project demonstrates the power of Terraform as Infrastructure as Code (IaC) to automate the deployment and management of a scalable web server infrastructure on AWS. By utilizing Terraform's declarative syntax, we have successfully set up a web server infrastructure with auto-scaling capabilities, load balancing, and comprehensive monitoring using CloudWatch alarms. The IaC approach ensures consistency, reproducibility, and version control for the infrastructure, making it a valuable asset for any organization seeking to manage their AWS resources efficiently and securely.

Feel free to contact me if you have any questions or feedback on this project. Happy learning!
