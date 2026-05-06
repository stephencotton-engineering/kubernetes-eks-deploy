# Kubernetes EKS Deployment — AWS

Production-style Kubernetes deployment on Amazon EKS. Implements a containerized application with horizontal pod autoscaling, health checks, and Helm-based configuration management.

---

## Architecture Overview

```
Internet
    │
    ▼
AWS Load Balancer
    │
    ▼
EKS Cluster
    │
    ▼
Kubernetes Service
    │
    ▼
Pod (container) × N replicas
    │
    ▼
HPA scales pods based on CPU
```

---

## What This Builds

- Amazon EKS cluster running Kubernetes
- Containerized application deployed via Kubernetes manifests
- Kubernetes Service exposing the application via a Load Balancer
- Horizontal Pod Autoscaler scaling pods based on CPU usage
- Helm chart for reusable, configurable deployments
- Liveness and readiness probes for container health checking
- Resource requests and limits enforced on all pods

---

## Project Structure

```
kubernetes-eks-deploy/
├── manifests/
│   ├── deployment.yaml       # Defines how the app runs
│   ├── service.yaml          # Exposes the app via load balancer
│   └── hpa.yaml              # Horizontal Pod Autoscaler
├── helm/
│   └── app-chart/
│       ├── Chart.yaml        # Helm chart metadata
│       ├── values.yaml       # Default configuration values
│       └── templates/
│           ├── deployment.yaml
│           ├── service.yaml
│           └── hpa.yaml
└── README.md
```

---

## Prerequisites

- AWS CLI configured with appropriate credentials
- eksctl installed for cluster management
- kubectl installed and configured
- Helm 3 installed

---

## Usage

```bash
# Create EKS cluster
eksctl create cluster --name stephen-eks-cluster --region us-east-1 --nodes 2

# Apply Kubernetes manifests
kubectl apply -f manifests/

# Deploy using Helm
helm install my-app helm/app-chart/

# Check deployment status
kubectl get pods
kubectl get services
kubectl get hpa
```

---

## Key Concepts Demonstrated

- Kubernetes Deployments with replica management
- Service types and load balancer exposure
- Horizontal Pod Autoscaling based on CPU metrics
- Liveness and readiness health probes
- Resource requests and limits
- Helm charts for reusable deployments

---

## Stack

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=for-the-badge&logo=helm&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
