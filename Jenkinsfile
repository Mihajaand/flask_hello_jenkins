pipeline {

    agent none

    stages {

        stage('Test') {
            agent {
                docker {
                    image 'python:3.11'
                    args '-u root'
                }
            }
            steps {
                sh 'python -m pip install -r requirements.txt'
                sh 'python test.py'
            }
        }

        stage('Build Docker Image') {
            agent any
            steps {
                sh 'docker build -t localhost:4000/flask_hello:latest .'
            }
        }

        stage('Push Docker Image') {
            agent any
            steps {
                sh 'docker push localhost:4000/flask_hello:latest'
            }
        }
        stage('Deploy Kubernetes') {
            agent any

            steps {
                sh 'kubectl apply -f kubernetes/deployment.yaml'
                sh 'kubectl apply -f kubernetes/service.yaml'
            }
        }

    }
}