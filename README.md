# Deploying-MernApp-on-K8s


Highlighting the content

The repository includes configurations, scripts, and documentation for replicating the steps from Monica's tutorial on deploying a MERN stack application on Kubernetes.

Mapping the process

I’m organizing the repository with configurations, scripts, and documentation for deploying a MERN stack app on Kubernetes, covering prerequisites, setup, and project structure.

Setting up the environment

First, clone the repository and start Minikube to launch the local Kubernetes cluster. Then, build the Docker images for the MERN app. Finally, apply the Kubernetes configurations to deploy the app, in sequence.

Verifying application status

I’m curious about confirming the deployment by checking the status of pods and services. This ensures everything is running smoothly and as expected in the local Kubernetes cluster.

Verifying deployment

I’m checking the deployment details for the MERN app, including Kubernetes configurations for deployment, service, secrets, and node port. Also, exploring how to access the app through Minikube.

markdown
Copy
Edit
# MERN App on Kubernetes

A practical, hands-on project for deploying a full-stack MERN (MongoDB, Express, React, Node.js) application using Kubernetes. This repository contains all the configuration files, Docker setup, and instructions to replicate the deployment process as demonstrated in the [Complete Kubernetes Course | Deploy MERN app](https://www.youtube.com/embed/7XDeI5fyj3w?autoplay=1) video by [Monica](https://monica.im).

---

## Overview

This project is designed to help beginners learn Kubernetes by deploying a ready-made MERN application. The focus is on understanding and applying key Kubernetes concepts such as:

- **Worker Nodes & Control Plane:** Using `kubectl` to interact with Kubernetes.
- **Deployments:** Configuring and managing application deployments.
- **Secrets Management:** Securely handling sensitive information (e.g., MongoDB credentials).
- **Services & NodePort:** Exposing applications internally and externally, including load balancing.
- **Minikube:** Running a local Kubernetes cluster for testing and development.

---

## Project Structure

mern-k8s-deployment/ ├── k8s/ │ ├── deployment.yaml # Kubernetes deployment configuration for the MERN app │ ├── service.yaml # Service configuration for exposing the MERN app │ ├── secrets.yaml # Secrets configuration for managing MongoDB credentials │ └── nodeport.yaml # NodePort configuration for external access ├── docker/ │ ├── Dockerfile # Dockerfile for building the MERN app container │ └── ... # Additional Docker configuration files (if any) ├── README.md # This file └── .gitignore # Specifies files and directories to be ignored by Git

yaml


---

## Prerequisites

Before setting up the project, ensure you have the following installed:

- **Docker:** [Get Docker](https://www.docker.com/get-started)
- **Kubernetes CLI (`kubectl`):** [Install kubectl](https://kubernetes.io/docs/tasks/tools/)
- **Minikube:** [Install Minikube](https://minikube.sigs.k8s.io/docs/start/)
- **Basic knowledge of Docker and Kubernetes concepts**

---

## Setup Instructions

### 1. Clone the Repository

Clone the repository to your local machine:

```bash
git clone https://github.com/yourusername/mern-k8s-deployment.git
cd mern-k8s-deployment
2. Start Minikube
Start your local Kubernetes cluster using Minikube:

bash:
minikube start
If you want to use Minikube’s Docker daemon (so that images are available to Minikube), run:

bash:
eval $(minikube docker-env)

3. Build the Docker Image
Build the Docker image for the MERN app:

bash:
docker build -t yourusername/mern-app:latest -f docker/Dockerfile .

4. Apply Kubernetes Configurations
Deploy the application components by applying the YAML configuration files in the following order:

Secrets:
Manage MongoDB credentials and other sensitive data.

bash:
kubectl apply -f k8s/secrets.yaml

Deployment:
Create and manage the application pods.

bash:
kubectl apply -f k8s/deployment.yaml

Service:
Expose the application internally via a stable IP and DNS name.

bash:
kubectl apply -f k8s/service.yaml

NodePort (Optional):
Expose the service externally using a NodePort.

bash:
kubectl apply -f k8s/nodeport.yaml

5. Verify the Deployment
Check that the pods and services are running:

bash:
kubectl get pods
kubectl get services

6. Access the Application
If you deployed using NodePort or want to test locally via Minikube, you can retrieve the service URL:

bash:
minikube service <service-name>
Replace <service-name> with the name of your deployed service.

Kubernetes Configuration Details
Deployment (k8s/deployment.yaml):
Sets the API version, metadata, replica count, and container specifications for the MERN app.

Service (k8s/service.yaml):
Provides a consistent endpoint (IP/DNS) for accessing the application pods and handles load balancing.

Secrets (k8s/secrets.yaml):
Securely manages sensitive data like MongoDB credentials using best practices.

NodePort (k8s/nodeport.yaml):
Exposes the service on a specific port, allowing external traffic to access the application.

Contributing
Contributions are welcome! If you have improvements, bug fixes, or additional features to suggest, please follow these steps:

Fork the repository.
Create a new branch for your feature or bug fix.
Commit your changes with clear messages.
Open a pull request with a description of your changes.
