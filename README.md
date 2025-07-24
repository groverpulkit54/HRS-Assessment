# HRS-Assessment

# AWS Jenkins Infrastructure with Terraform

## Overview

This project sets up a basic CI/CD infrastructure on AWS using **Terraform**. The goal is to provision a highly available, secure, and scalable Jenkins environment hosted on an **EC2 instance** behind an **Application Load Balancer (ALB)** inside a **VPC**. The Terraform state is managed remotely using **Amazon S3**.

## Architecture

Below is the high-level architecture deployed by this Terraform setup:

### Components Explained:

- **VPC (Virtual Private Cloud)**  
  A logically isolated network where all resources reside. It includes both public and private subnets.

- **Public Subnet**  
  Hosts the **Application Load Balancer (ALB)** to accept incoming requests from clients.

- **Private Subnet**  
  Contains the **EC2 instance** where **Jenkins** is installed and configured. This ensures that Jenkins is not directly exposed to the internet.

- **Application Load Balancer (ALB)**  
  Routes incoming web traffic to the Jenkins EC2 instance. ALB is internet-facing and lives in the public subnet.

- **EC2 Instance (Jenkins)**  
  This server runs Jenkins and handles build and deployment jobs triggered via webhooks or pipelines.

- **Amazon S3 Bucket**  
  Stores the Terraform state file remotely, ensuring state persistence and team collaboration.

- **GitHub**  
  Acts as a version control and source for triggering Jenkins pipelines (e.g., via webhook or Git pull).

## Terraform Features Used

- Remote state management using S3.
- Resource provisioning for:
  - VPC
  - Subnets
  - ALB
  - EC2 instance with Jenkins installed
  - Security groups for access control

