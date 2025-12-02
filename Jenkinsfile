pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/Sodhu1008/devops.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t local-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop local-app-container || true
                docker rm local-app-container || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d --name local-app-container -p 3000:3000 local-app'
            }
        }
    }
}