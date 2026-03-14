pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/ghediyakrupali06/DevOps-CI-CD-Pipeline-project.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker run -d -p 5000:5000 devops-app'
            }
        }

    }
}