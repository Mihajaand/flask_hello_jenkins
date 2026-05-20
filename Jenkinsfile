pipeline {
    agent any

    stages {

        stage('Test') {
            steps {
                sh 'pip install -r requirements.txt'
                sh 'python3 test.py'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t localhost:4000/flask_hello:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push localhost:4000/flask_hello:latest'
            }
        }

    }
}