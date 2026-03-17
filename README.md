# DevOps-CI-CD-Pipeline-project
DevOps CI/CD Pipeline with Jenkins, Docker & Kubernetes
1. Project Overview

This project demonstrates a fully automated CI/CD pipeline for deploying applications using Jenkins, Docker, and Kubernetes.
Whenever code is pushed to GitHub, the pipeline automatically builds, tests, dockerizes, and deploys the application to a Kubernetes cluster.

Tech Stack:

Jenkins

GitHub

Docker

Kubernetes (Minikube)

2. Features

Automated build on code commit

Unit testing and simple validation

Docker image creation and push to DockerHub

Deployment on Kubernetes

Service exposure via LoadBalancer (Minikube)

3. Architecture Diagram


GitHub → Jenkins → Docker → Kubernetes → Application Deployment

4. Prerequisites

Git installed

Docker installed and running

Jenkins installed

Minikube / Kubernetes cluster

DockerHub account
