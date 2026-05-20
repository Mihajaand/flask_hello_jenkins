pipeline {

    agent {
        docker {
            image 'python:3.11'
            args '-u root'
        }
    }

    stages {

        stage('Test') {
            steps {
                sh 'pip install -r requirements.txt'
                sh 'python test.py'
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