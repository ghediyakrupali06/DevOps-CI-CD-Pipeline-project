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
5. Setup / Installation Steps

Step 1: Clone the repository

git clone <your_repo_url>
cd <project_directory>

Step 2: Jenkins Setup

Open Jenkins dashboard → Manage Jenkins → Manage Plugins → Install: Git, Docker, Kubernetes plugins

Create a New Pipeline → Point to your GitHub repository

Configure credentials (GitHub, DockerHub)

Step 3: Docker Build & Push

docker build -t <dockerhub_username>/<image_name>:latest .
docker push <dockerhub_username>/<image_name>:latest

Step 4: Kubernetes Deployment
Apply deployment and service YAML files:

kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml

Step 5: Access Application

minikube service <service_name>

Open the URL displayed to access your deployed application.

6. Jenkins Pipeline (Jenkinsfile)

Here’s an example of the CI/CD pipeline used:

pipeline {
    agent any
    environment {
        DOCKER_IMAGE = "<dockerhub_username>/<image_name>:latest"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: '<your_repo_url>'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }
        stage('Push to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub_creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'
                sh 'kubectl apply -f k8s/service.yaml'
            }
        }
    }
    post {
        success {
            echo 'Deployment Successful!'
        }
        failure {
            echo 'Pipeline Failed!'
        }
    }
}
7. Screenshots / Demo

Jenkins Pipeline running

Docker image in DockerHub

Kubernetes pods and service

Application UI in browser

8. Technologies Used

CI/CD: Jenkins

Version Control: GitHub

Containerization: Docker

Orchestration: Kubernetes (Minikube)

Cloud (optional): AWS / GCP

9. Author

Krupali Ghediya

LinkedIn: https://www.linkedin.com/in/krupali-ghediya

GitHub: https://github.com/ghediyakrupali06

10. License

This project is licensed under the MIT License.
