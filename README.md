# CI/CD Auto-Scaling Infrastructure Pipeline `[DEVOPS]`

An automated, high-availability deployment pipeline designed to streamline the transition from code to production while maintaining 99.9% uptime through intelligent scaling.

### 🚀 Key Features
* **Automated Workflow:** Seamless integration from **GitHub** to **AWS EC2** via **Jenkins**.
* **Performance:** Reduced manual deployment time by **60%** through full automation.
* **Scalability:** Implemented **Auto-Scaling Groups (ASG)** and **Elastic Load Balancers (ELB)** to handle **500+ concurrent connections**.
* **Deployment Strategy:** Blue-Green deployment model with **automated rollback** triggers.
* **Infrastructure as Code:** Managed entirely via **Terraform**.

### 🛠 Tech Stack
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=flat&logo=amazon-aws&logoColor=white) ![Terraform](https://img.shields.io/badge/Terraform-%235835CC.svg?style=flat&logo=terraform&logoColor=white) ![Jenkins](https://img.shields.io/badge/Jenkins-%23D24939.svg?style=flat&logo=jenkins&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-%232088FF.svg?style=flat&logo=github-actions&logoColor=white)




# Scalable Cloud Infrastructure Automation `[INFRA]`

A robust, fault-tolerant AWS infrastructure solution focused on automation, state consistency, and deep observability.

### 📊 Infrastructure Architecture
```mermaid
graph TD
    A[Users] --> B[AWS Load Balancer]
    B --> C[Auto Scaling Group]
    C --> D1[EC2 Instance 1]
    C --> D2[EC2 Instance 2]
    C --> D3[EC2 Instance 3]
    D1 --> E[Node Exporter]
    D2 --> E
    D3 --> E
    E --> F[Prometheus]
    F --> G[Grafana Dashboards]
