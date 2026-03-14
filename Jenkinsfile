pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'git 'https://github.com/ghediyakrupali06/DevOps-CI-CD-Pipeline-project.git''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5000:5000 devops-app'
            }
        }

    }
}