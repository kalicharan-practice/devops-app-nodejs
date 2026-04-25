pipeline {
    agent any

    tools {
        nodejs 'node18'
    }

    environment {
        KUBECONFIG = '/root/.kube/config'
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/kalicharan-practice/devops-app-nodejs.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-app .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl version --client'
                sh 'kubectl get nodes'
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}