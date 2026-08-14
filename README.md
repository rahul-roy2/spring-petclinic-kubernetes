# spring-petclinic-kubernetes
# Spring PetClinic - Kubernetes DevOps Deployment

## Project Overview

This project demonstrates the deployment of the Spring PetClinic application using Docker, Jenkins CI/CD and Kubernetes on an AWS EC2 instance.

The project covers containerization, CI/CD, Kubernetes deployment, service exposure, NGINX Ingress, horizontal pod autoscaling and Kubernetes resource monitoring.

---

## Architecture

```text
Developer
   |
   | Git Push
   v
GitHub
   |
   v
Jenkins
   |
   | Maven Build
   | Docker Build
   v
Docker Image
   |
   v
Docker Hub
   |
   v
Kubernetes Cluster
   |
   +-------------------------+
   |                         |
   v                         v
Deployment              NGINX Ingress
   |                         |
   |                         v
   |                  Kubernetes Service
   |                         |
   +----------+--------------+
              |
              v
       Spring PetClinic Pods
              |
              v
          Port 8080
