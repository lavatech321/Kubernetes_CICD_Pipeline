# 🚀 Full Stack Kubernetes CI/CD Deployment using Terraform, Ansible & Jenkins

This project demonstrates complete automation of deploying a full-stack application on Kubernetes using Terraform, Ansible, Jenkins, Docker, and Minikube.

The infrastructure is provisioned on AWS EC2 using Terraform. Ansible automatically installs Jenkins, Docker, and Kubernetes Minikube. Jenkins CI/CD pipeline then deploys a full-stack application consisting of:

- MySQL Database
- Spring Boot Backend
- ReactJS Frontend

---

# 📌 Project Overview

This project automates the complete DevOps workflow from infrastructure provisioning to Kubernetes deployment.

## Workflow

1. Terraform launches AWS EC2 instance
2. Terraform triggers Ansible playbook
3. Ansible installs:
   - Docker
   - Jenkins
   - Kubernetes Minikube
4. Jenkins CI/CD pipeline deploys application on Kubernetes
5. ReactJS frontend communicates with Spring Boot backend
6. Spring Boot backend connects to MySQL database

---

# 🏗️ Architecture Diagram

```text
                    ┌────────────────────┐
                    │     Terraform      │
                    │────────────────────│
                    │ Launch AWS EC2     │
                    └─────────┬──────────┘
                              │
                              ▼
                 ┌────────────────────────┐
                 │        Ansible         │
                 │────────────────────────│
                 │ Install Jenkins        │
                 │ Install Docker         │
                 │ Install Minikube       │
                 └─────────┬──────────────┘
                           │
                           ▼
                 ┌────────────────────────┐
                 │    Jenkins CI/CD       │
                 │────────────────────────│
                 │ Pull GitHub Code       │
                 │ Build Docker Images    │
                 │ Deploy to Kubernetes   │
                 └─────────┬──────────────┘
                           │
        ┌──────────────────┼──────────────────┐
        ▼                  ▼                  ▼
┌──────────────┐  ┌────────────────┐  ┌────────────────┐
│ MySQL DB     │  │ Spring Backend │  │ React Frontend │
│ Kubernetes   │  │ Kubernetes Pod │  │ Kubernetes Pod │
└──────────────┘  └────────────────┘  └────────────────┘
                           │
                           ▼
                 ┌────────────────────────┐
                 │   Kubernetes Cluster   │
                 │       (Minikube)       │
                 └────────────────────────┘
```

---

# ⚙️ Technologies Used

| Technology | Purpose |
|------------|----------|
| Terraform | Infrastructure Provisioning |
| AWS EC2 | Cloud Hosting |
| Ansible | Configuration Management |
| Jenkins | CI/CD Automation |
| Docker | Containerization |
| Kubernetes | Container Orchestration |
| Minikube | Local Kubernetes Cluster |
| MySQL | Database |
| Spring Boot | Backend API |
| ReactJS | Frontend UI |
| Linux | Server Environment |

---

# 🚀 Deployment Flow

```text
Terraform Launches AWS EC2
              │
              ▼
Ansible Configures Server
              │
              ├── Install Jenkins
              ├── Install Docker
              ├── Install Kubernetes
              └── Configure Environment
              │
              ▼
Jenkins Pipeline Starts
              │
              ├── Pull Source Code
              ├── Build Docker Images
              ├── Create Kubernetes Deployments
              └── Deploy Full Stack App
              │
              ▼
Kubernetes Cluster Running:
    ├── MySQL Database
    ├── Spring Boot Backend
    └── ReactJS Frontend
```

---

# ☁️ Infrastructure Deployment

## Configure Terraform Variables

Update the `terraform.tfvars` file with your AWS credentials.

```bash
% cat terraform.tfvars

AWS_ACCESS_KEY=""
AWS_SECRET_KEY=""
AWS_REGION="us-east-1"
```

## Initialize Terraform

```bash
terraform init
```

## Apply Infrastructure

```bash
terraform apply --auto-approve
```

## Destroy Infrastructure

```bash
terraform destroy --auto-approve
```

---

# 🔧 Ansible Automation

Ansible automatically configures the EC2 server by installing:

- Docker
- Jenkins
- Kubernetes Minikube
- Required dependencies

---

# ⚙️ Jenkins CI/CD Pipeline

Jenkins pipeline automates:

- Source code pull from GitHub
- Docker image build
- Kubernetes deployment
- Application rollout

---

# ☸️ Kubernetes Deployment

The application is deployed inside Kubernetes pods.

## Kubernetes Components

| Component | Purpose |
|-----------|----------|
| MySQL Pod | Database Service |
| Backend Pod | Spring Boot API |
| Frontend Pod | ReactJS UI |
| Services | Internal Communication |

---

# 📤 Terraform Outputs

After deployment, Terraform provides useful access details.

---

## 🔐 EC2 Access

```bash
ssh -i ~/.ssh/id_rsa ubuntu@<EC2-PUBLIC-IP>
```

---

## 🌐 Jenkins UI

```text
http://<EC2-PUBLIC-IP>:8080
```

---

## ☸️ Kubernetes Deployment Verification

```bash
kubectl get pods
```

---

## 🛢️ MySQL Database Access

```bash
mysql -uappuser -papppass appdb
```

---

## 🚀 Application Access

## ReactJS Frontend

```text
http://<EC2-PUBLIC-IP>:30000
```

---

## 📌 Terraform Output Example

```text
Kubernetes-Application-Deployment:
kubectl get pods

MYsql-Live:
mysql -uappuser -papppass appdb

Export-port-to-access-the-application:
kubectl port-forward service/frontend 30000:3000 --address 0.0.0.0 &

kubectl port-forward service/backend 30081:7081 --address 0.0.0.0 &

App-Live:
http://<EC2-PUBLIC-IP>:30000

EC2-Instance-access-details:
ssh -i ~/.ssh/id_rsa ubuntu@<EC2-PUBLIC-IP>

Jenkins-UI:
http://<EC2-PUBLIC-IP>:8080
```

---
