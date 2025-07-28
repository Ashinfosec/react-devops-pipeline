# react-devops-pipeline 

A complete DevOps demonstration project showcasing CI/CD pipeline implementation with security scanning and quality analysis.

## 🏗️ Architecture Overview

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│    BUILD    │───▶│   DOCKER    │───▶│  SONARQUBE  │
│             │    │             │    │             │
│ • Vite Build│    │ • Image     │    │ • Code      │
│ • npm audit │    │ • Trivy     │    │   Quality   │
│ • Tests     │    │   Security  │    │ • Security  │
│             │    │   Scan      │    │   Analysis  │
└─────────────┘    └─────────────┘    └─────────────┘
```

## 🛠️ Technology Stack

- **Frontend**: React + Vite
- **CI/CD**: Azure DevOps Pipelines
- **Containerization**: Docker
- **Security Scanning**: Trivy (container vulnerabilities)
- **Code Quality**: SonarQube
- **Infrastructure**: Self-hosted Azure DevOps agent

## 🔄 Pipeline Stages

### Stage 1: Build & Test
- Node.js 18.x setup
- Dependency installation
- Security audit (`npm audit`)
- Vite build process
- Artifact publishing

### Stage 2: Docker & Security
- Docker image creation
- Trivy vulnerability scanning
- Image tagging with build ID
- Automated cleanup

### Stage 3: Code Quality
- SonarQube analysis
- Security hotspot detection
- Code coverage reporting
- Quality gate validation

## 🔒 Security Features

- **Container Scanning**: Trivy identifies vulnerabilities in Docker images
- **Code Analysis**: SonarQube detects security issues and code smells
- **Secret Management**: Azure DevOps Variable Groups for token security
- **Automated Auditing**: npm audit for dependency vulnerabilities

## 📊 Quality Metrics

Current project status:
- **Security Rating**: E (1 critical issue to resolve)
- **Reliability Rating**: C (75 issues identified)
- **Maintainability Rating**: A (well-maintained codebase)
- **Test Coverage**: 0% (tests to be implemented)
- **Duplications**: 0% (no code duplication)

## 🚀 Getting Started

### Prerequisites
- Azure DevOps account
- Self-hosted Azure DevOps agent
- Docker installed
- SonarQube running locally
- Node.js 18.x

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/tarkov-helper-devops
   cd tarkov-helper-devops
   ```

2. **Set up SonarQube**
   ```bash
   docker run -d --name sonarqube -p 9000:9000 sonarqube:latest
   ```

3. **Configure Azure DevOps**
   - Import the `azure-pipelines.yml`
   - Set up Variable Group `Local-Secrets` with `SONAR_TOKEN`
   - Configure self-hosted agent

4. **Run the pipeline**
   - Push changes to trigger the pipeline
   - Monitor results in Azure DevOps

## 📁 Project Structure

```
├── src/                    # React source code
├── public/                 # Static assets
├── dist/                   # Build output
├── azure-pipelines.yml     # CI/CD pipeline definition
├── Dockerfile             # Container configuration
├── package.json           # Node.js dependencies
└── README.md              # This file
```

## 🔧 Pipeline Configuration

The pipeline is defined in `azure-pipelines.yml` and includes:

- **Parallel execution** of Docker and SonarQube stages
- **Artifact management** for build outputs
- **Security scanning** integration
- **Automated cleanup** to prevent disk space issues
- **Error handling** with `continueOnError` flags

## 📈 Monitoring & Reporting

- **Azure DevOps**: Pipeline execution logs and artifacts
- **SonarQube Dashboard**: http://localhost:9000
- **Trivy Reports**: Container vulnerability details
- **Build Artifacts**: Stored in Azure DevOps

## 🎯 Learning Outcomes

This project demonstrates:
- **CI/CD Pipeline Design**: Multi-stage pipeline architecture
- **Security Integration**: Vulnerability scanning at multiple levels
- **Quality Assurance**: Automated code quality checks
- **DevOps Best Practices**: Secret management, artifact handling
- **Containerization**: Docker image creation and scanning
