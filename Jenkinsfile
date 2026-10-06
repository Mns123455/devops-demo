
pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-python-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop my-python-container || true'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm my-python-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name my-python-container my-python-app'
            }
        }
    }
}
