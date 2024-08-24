# Deploying-Static-Website-Using-Kubernetes
Deploying a static website using Kubernetes. This project introduces you to the basics of Kubernetes concepts like Pods, Deployments, and Services. 
This project demonstrates how to deploy a static website using Kubernetes on a Minikube cluster. It includes a simple Nginx-based static website and exposes it via a Kubernetes NodePort service.

Project Overview
Application: Static website served by Nginx.
Container Image: Custom Docker image based on nginx:alpine.
Deployment: Managed using a Kubernetes Deployment.
Service: Exposed using a Kubernetes Service of type NodePort.
Prerequisites
Minikube installed and running.
kubectl command-line tool configured to interact with Minikube.
Docker installed (for building the Docker image).
Setup Instructions
1. Start Minikube
If Minikube is not already running, start it with: 
minikube start
2. Configure Docker to Use Minikube’s Docker Daemon
To build Docker images within Minikube’s environment, run: 
eval $(minikube -p minikube docker-env)
3. Create the Docker Image
Create a Dockerfile with the following content:
FROM nginx:alpine
COPY . /usr/share/nginx/html
4. Create Deployment and Service Files
Create a deployment.yaml file:
Create a service.yaml file:
5. Apply the Kubernetes Configuration
Deploy the application and service:
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
6. Access the Application
Retrieve the Minikube IP address:
minikube ip
Project Structure
Dockerfile: Defines the Docker image for the static website.
deployment.yaml: Kubernetes Deployment configuration for the static website.
service.yaml: Kubernetes Service configuration to expose the deployment.
Troubleshooting
Pods not starting: Check the logs with kubectl logs <pod-name> and inspect events with kubectl describe pod <pod-name>.
ImagePullBackOff: Ensure that the image is correctly built and available in Minikube’s Docker environment.
Cannot access application: Verify that the service is correctly exposed and the NodePort is correctly configured.
