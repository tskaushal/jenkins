# DevOps Infrastructure Projects

This repository showcases two DevOps projects focused on:

- CI/CD Automation
- Infrastructure as Code
- AWS Auto Scaling
- Monitoring with Prometheus and Grafana

---

# Project 1 — CI/CD Auto-Scaling Infrastructure Pipeline

## Overview

This project implements a complete CI/CD pipeline that automatically builds, tests, and deploys an application to AWS infrastructure using Terraform and Jenkins/GitHub Actions.

---

## Tech Stack

- AWS (EC2, Load Balancer, Auto Scaling)
- Terraform
- Jenkins
- GitHub Actions
- Linux
- Docker (optional)

---

## Architecture Diagram

```mermaid
flowchart TD

A[Developer] --> B[GitHub Repository]

B --> C[CI Pipeline]

C --> D[Checkout Code]
C --> E[Build Application]
C --> F[Run Tests]
C --> G[Docker Build]

C --> H[Terraform Plan]
H --> I[Terraform Apply]

I --> J[AWS Infrastructure]

J --> K[Application Load Balancer]
K --> L[Auto Scaling Group]
L --> M[EC2 Instances]

Remote Terraform State

Terraform state is stored using:

S3 Bucket → State storage

DynamoDB → State locking

Example backend configuration:

terraform {
  backend "s3" {
    bucket         = "terraform-state-bucket"
    key            = "infra/terraform.tfstate"
    region         = "ap-south-1"
    dynamodb_table = "terraform-lock"
  }
}
Monitoring Pipeline

Metrics collection flow:

EC2 Instances
      │
      ▼
Node Exporter
      │
      ▼
Prometheus
      │
      ▼
Grafana Dashboards
