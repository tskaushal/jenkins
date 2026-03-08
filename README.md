```markdown
# DevOps Infrastructure Projects

This repository showcases two DevOps projects focused on **CI/CD automation**, **Infrastructure as Code**, **auto-scaling systems**, and **cloud monitoring** using modern DevOps tools.

---

# Project 1: CI/CD Auto-Scaling Infrastructure Pipeline

## Overview

This project implements a complete **CI/CD pipeline** that automatically builds, tests, and deploys an application to AWS infrastructure. The system supports **auto-scaling**, **load balancing**, and **blue-green deployments** to ensure high availability and minimal downtime.

## Tech Stack

- AWS (EC2, Load Balancer, Auto Scaling)
- Terraform (Infrastructure as Code)
- Jenkins
- GitHub Actions
- Linux
- Docker (optional)

---

## Architecture Diagram

```

Developer
│
▼
GitHub Repository
│
▼
GitHub Actions / Jenkins Pipeline
│
├── Checkout Code
├── Build
├── Run Tests
└── Docker Build (optional)
│
▼
Terraform Deployment
│
▼
AWS Infrastructure
│
▼
Application Load Balancer
│
▼
Auto Scaling Group
│
▼
EC2 Instances

```

---

## CI/CD Pipeline Flow

### Step 1 — Code Push

The developer pushes code to GitHub.

```

git push origin main

```

This triggers the CI/CD pipeline.

---

### Step 2 — Pipeline Execution

The CI pipeline performs the following steps:

```

1. Checkout Repository
2. Build Application
3. Run Tests
4. Docker Build (optional)
5. Terraform Plan
6. Terraform Apply
7. Deploy Application

```

---

### Step 3 — Infrastructure Provisioning

Terraform provisions AWS infrastructure including:

```

VPC
Subnets
Security Groups
EC2 Instances
Auto Scaling Group
Application Load Balancer

```

---

### Step 4 — Application Deployment

After infrastructure provisioning:

```

Users
│
▼
AWS Load Balancer
│
▼
Auto Scaling Group
│
▼
EC2 Instances running the application

```

---

### Step 5 — Auto Scaling

The system automatically scales based on load:

```

CPU > Threshold
│
▼
Auto Scaling launches new EC2 instance

```

Example configuration:

```

Minimum instances: 2
Desired instances: 3
Maximum instances: 5

```

---

### Step 6 — Blue-Green Deployment

Two deployment environments are maintained:

```

Blue  → Current Production
Green → New Version

```

Deployment process:

```

Deploy new version → Green environment
Test Green environment
Switch load balancer traffic
Deactivate Blue environment

```

This ensures **zero downtime deployment**.

---

# Project 2: Scalable Cloud Infrastructure Automation

## Overview

This project automates the provisioning of **scalable AWS infrastructure** using Terraform and implements a **full monitoring stack** with Prometheus and Grafana.

The infrastructure supports:

- Auto scaling
- Infrastructure as Code
- Remote Terraform state management
- Monitoring and observability

---

## Tech Stack

- AWS (EC2, VPC, Load Balancer, Auto Scaling)
- Terraform
- Prometheus
- Node Exporter
- Grafana
- Linux

---

## Infrastructure Architecture

```

Users
│
▼
AWS Load Balancer
│
▼
Auto Scaling Group
│
▼
EC2 Instances
│
▼
Node Exporter
│
▼
Prometheus
│
▼
Grafana Dashboard

```

---

## Terraform Infrastructure Setup

Terraform is used to define infrastructure as code.

Project structure:

```

terraform/
│
├── main.tf
├── variables.tf
├── outputs.tf
├── vpc.tf
├── autoscaling.tf
├── monitoring.tf
└── backend.tf

```

---

## Terraform Execution Flow

### Initialize Terraform

```

terraform init

```

### Preview Infrastructure Changes

```

terraform plan

```

### Provision Infrastructure

```

terraform apply

```

Terraform provisions:

```

VPC
Subnets
Security Groups
EC2 Instances
Auto Scaling Groups
Load Balancer
Monitoring Components

```

---

## Remote Terraform State

Terraform state is stored remotely to support team collaboration.

```

S3 Bucket → Stores Terraform state
DynamoDB  → Provides state locking

```

Example backend configuration:

```

terraform {
backend "s3" {
bucket         = "terraform-state-bucket"
key            = "infra/terraform.tfstate"
region         = "ap-south-1"
dynamodb_table = "terraform-lock"
}
}

```

---

## Monitoring Setup

Each EC2 instance runs **Node Exporter**.

```

EC2 Instance
│
▼
Node Exporter

```

Node Exporter exposes system metrics such as:

```

CPU usage
Memory usage
Disk usage
Network statistics

```

---

## Prometheus Monitoring Flow

Prometheus collects metrics from all instances.

```

EC2 Instances
│
▼
Node Exporter
│
▼
Prometheus Server

```

Prometheus stores metrics and provides query capabilities.

---

## Grafana Visualization

Grafana connects to Prometheus and visualizes infrastructure metrics.

Example dashboards include:

```

CPU Usage
Memory Usage
Network Traffic
Disk Usage
System Load
Instance Health

```

Monitoring flow:

```

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



