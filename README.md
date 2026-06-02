# 🚀 DevOps Pipeline Demo

[![CI Pipeline](https://github.com/YOUR_USERNAME/devops-pipeline-demo/actions/workflows/ci.yaml/badge.svg)](https://github.com/YOUR_USERNAME/devops-pipeline-demo/actions/workflows/ci.yaml)
[![CD Pipeline](https://github.com/YOUR_USERNAME/devops-pipeline-demo/actions/workflows/cd.yaml/badge.svg)](https://github.com/YOUR_USERNAME/devops-pipeline-demo/actions/workflows/cd.yaml)
[![Docker Pulls](https://img.shields.io/docker/pulls/YOUR_USERNAME/devops-pipeline-demo)](https://hub.docker.com/r/YOUR_USERNAME/devops-pipeline-demo)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

A **production-grade CI/CD pipeline demonstration** showcasing modern DevOps practices including continuous integration, continuous deployment, containerization, and Kubernetes orchestration.

## 🎯 What This Project Demonstrates

- ✅ **Continuous Integration**: Automated testing, linting, security scanning on every commit
- ✅ **Continuous Deployment**: Automatic Docker image building and Kubernetes deployment
- ✅ **Containerization**: Multi-stage Docker builds for optimized images
- ✅ **Orchestration**: Kubernetes deployments with health checks and auto-scaling ready
- ✅ **Infrastructure as Code**: Complete Kubernetes manifests version controlled
- ✅ **Developer Experience**: Makefile, docker-compose, and comprehensive documentation
- ✅ **Security**: Vulnerability scanning, non-root containers, and secret management

## 🏗️ Architecture
┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│ GitHub │────▶│ GitHub │────▶│ Docker │────▶│ Kubernetes │
│ Commit │ │ Actions CI │ │ Hub │ │ Cluster │
└─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘
│ │ │
▼ ▼ ▼

Lint & Test - Image Tagging - Rolling Update

Security Scan - Versioning - Health Check

Build Image - Registry Push - Auto-scaling

## 📋 Prerequisites

- Docker Desktop or Docker Engine
- Python 3.11+ (for local development)
- kubectl (for Kubernetes deployment)
- Docker Hub account (for image registry)

## 🚀 Quick Start

### Local Development

# Clone the repository
git clone https://github.com/YOUR_USERNAME/devops-pipeline-demo.git
cd devops-pipeline-demo

# Run locally with Python
make build
make run

# Or use Docker Compose
docker-compose up

# Test the application
curl http://localhost:5000/
curl http://localhost:5000/health

Run with Docker
# Build the image
make docker-build

# Run the container
make docker-run

# Test the running container
curl http://localhost:5000/

Deploy to Kubernetes
# Update k8s/deployment.yaml with your Docker Hub username
# Then deploy
make k8s-deploy

# Check deployment status
kubectl get pods -n devops-demo
kubectl get services -n devops-demo
🔧 CI/CD Pipeline Details
Continuous Integration (CI)
Trigger: Pull requests and pushes to main/develop

Stages:

Code checkout
Python dependency installation
Linting with flake8
Formatting check with black
Unit tests with pytest (with coverage)
Security scan with Trivy
Docker image build test
Continuous Deployment (CD)
Trigger: Pushes to main or tags (v*)

Stages:

Version extraction (from git tag or commit SHA)
Docker image build with BuildKit
Multi-platform build support
Push to Docker Hub with multiple tags
Kubernetes manifest update
Rolling deployment to cluster
Health check verification
🔐 Required GitHub Secrets
For the CD pipeline to work, configure these secrets in your GitHub repository:

Secret Name	Description
DOCKER_HUB_USERNAME	Your Docker Hub username
DOCKER_HUB_TOKEN	Docker Hub personal access token
KUBE_CONFIG	Base64-encoded kubeconfig file

Setting up Kubernetes Secret
# Encode your kubeconfig
cat ~/.kube/config | base64 | pbcopy  # macOS
cat ~/.kube/config | base64 -w 0 | xclip  # Linux

# Add the output as KUBE_CONFIG secret in GitHub
📊 Monitoring & Observability
The application exposes several endpoints for monitoring:

GET / - Main application endpoint (returns JSON with version and hostname)

GET /health - Health check endpoint for Kubernetes probes

GET /metrics - Metrics endpoint for Prometheus scraping

🧪 Testing
# Run unit tests
make test

# Run with coverage
pytest app/test_app.py --cov=app/ --cov-report=html

# Open coverage report
open htmlcov/index.html
📈 Performance Considerations
Multi-stage builds: Reduces final image size by ~40%

Layer caching: Optimized Dockerfile for faster builds

Resource limits: Kubernetes requests/limits for stability

Health checks: Automatic recovery of unhealthy pods

Rolling updates: Zero-downtime deployments

🔒 Security Features
Non-root user in container (UID 1000)

Security scanning in CI pipeline

No sensitive data in images

Network policies ready (not implemented for demo)

Regular dependency updates via Dependabot

🎓 Learning Outcomes
By studying this repository, you'll understand:

How to structure a production-ready DevOps project

Best practices for GitHub Actions CI/CD

Multi-stage Docker builds optimization

Kubernetes deployment strategies

Security integration in CI pipelines

Professional documentation standards

🤝 Contributing
This is a demonstration project, but contributions are welcome! Please ensure:

All tests pass

Security scan passes

Documentation is updated

📝 License
MIT License - feel free to use this for learning and your own projects!

🙏 Acknowledgments
GitHub Actions for powerful CI/CD

Flask for the simple web framework

Kubernetes for container orchestration

Docker for containerization
