﻿# Production-Level-Blue-Green-Deployment
# Blue-Green Deployment Strategy in CI/CD DevSecOps Pipeline

## Project Overview
This project demonstrates the implementation of a **Blue-Green Deployment Strategy** within a CI/CD DevSecOps pipeline. It aims to ensure zero downtime and seamless transitions between application versions while embedding security and quality gates throughout the development lifecycle.

### Key Features:
- **Blue-Green Deployment**: Deploy applications in two separate environments (Blue and Green) to facilitate smooth updates.
- **CI/CD Pipeline**: Automated pipeline for building, testing, and deploying applications.
- **DevSecOps**: Integration of security tools like Trivy and SonarQube for continuous security scanning.

## Workflow

### 1. **Pipeline Stages**:
#### Pull Code
- Retrieve the latest code from the repository.

#### Maven Build and Test
- Compile the application and execute tests.

#### Trivy File System Scan
- Perform a static analysis of the source code for vulnerabilities.

#### SonarQube Analysis
- Analyze code quality and enforce quality gates.

#### Artifact Publication
- Package the application and publish it to Nexus.

#### Docker Build and Push
- Build a Docker image and push it to the Docker registry.

#### Trivy Docker Scan
- Scan the Docker image for vulnerabilities.

#### Kubernetes Deployment
- Deploy to Kubernetes using the Blue-Green strategy.

#### Traffic Switching
- Dynamically switch traffic between Blue and Green environments upon successful deployment.

### 2. **Tools and Technologies**:
- **Version Control**: Git
- **Build Tool**: Maven
- **Containerization**: Docker
- **Security Scanning**: Trivy, SonarQube
- **Artifact Repository**: Nexus
- **Orchestration**: Kubernetes (AKS)
- **CI/CD**: Jenkins

## Prerequisites
- **Kubernetes Cluster**: Ensure an AKS cluster is running.
- **Docker Hub Account**: Required for pushing Docker images.
- **Jenkins Setup**: Install Jenkins with necessary plugins (e.g., Kubernetes CLI, Maven, Docker, SonarQube, Trivy).
- **SonarQube Server**: Set up and configure.

## Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/Achref-dot-afk/Production-Level-Blue-Green-Deployment.git
```

### 2. Configure Jenkins
- Add credentials for Git, Docker Hub, and Kubernetes.
- Import the provided Jenkinsfile into your Jenkins pipeline.

### 3. Apply Kubernetes Configurations
Deploy required services and deployments:
```bash
kubectl apply -f AKS/manifests/mysql-ds.yml
kubectl apply -f AKS/manifests/bankapp-service.yml
```

### 4. Trigger the Pipeline
- Set the parameters for the deployment environment and Docker tag.
- Start the pipeline in Jenkins.

## Blue-Green Deployment Strategy
- **Blue Environment**: The currently active production environment.
- **Green Environment**: The new version of the application is deployed here.
- **Switch Traffic**: Update the Kubernetes service selector to route traffic to the Green environment once verified.

## Security Enhancements
- **Trivy FS & Docker Scans**: Detect vulnerabilities in code and Docker images.
- **SonarQube Quality Gates**: Enforce coding standards and reduce technical debt.

## Additional Notes
- Ensure proper resource allocation in AKS to avoid pending pods.
- Regularly monitor the pipeline's performance and security scans.
- I set up also RBAC for the AKS cluster to control access.

## Author
**Achref Habli**  
[achrefh1bli22@gmail.com](mailto:achrefh1bli22@gmail.com)

