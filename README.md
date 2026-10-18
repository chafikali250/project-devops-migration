# AWS EKS & Flask Application Migration Pipeline

An end-to-end DevOps pipeline that containerizes a Python Flask web application using Docker, provisions an AWS EKS (Kubernetes) cluster via Terraform (Infrastructure as Code), and automates CI/CD deployments using GitHub Actions.

---

## 🏗️ Architecture Overview

- **Application**: Lightweight Python Flask web application listening on `0.0.0.0:5000`.
- **Container Registry**: Amazon Elastic Container Registry (ECR) for hosting Docker images.
- **Infrastructure**: AWS EKS cluster running on 2x `t3.micro` worker nodes in the `eu-west-3` (Paris) region.
- **Networking**: Kubernetes Service of type `LoadBalancer` exposing the app publicly on port 80.
- **CI/CD Pipeline**: GitHub Actions for automated syntax testing, Docker container build, ECR push, and zero-downtime EKS deployment rollout.

---

## 📁 Repository Structure

```text
.
├── .github/
│   └── workflows/
│       └── deploy.yml          # GitHub Actions CI/CD workflow
├── app.py                      # Flask application entrypoint
├── Dockerfile                  # Container definition for the Flask app
├── main.tf                     # Terraform configuration for AWS EKS & networking
├── deployment.yaml            # Kubernetes Deployment manifest
├── service.yaml               # Kubernetes Service manifest (LoadBalancer)
├── requirements.txt            # Python dependencies
└── README.md                   # Project documentation
