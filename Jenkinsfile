pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git(
                    branch: 'main',
                    credentialsId: 'github-token',
                    url: 'https://github.com/Mns123455/devops-demo.git'
                )
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t devops-demo .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop devops-demo-container || true'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm devops-demo-container || true'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker run -d -p 5000:5000 --name devops-demo-container devops-demo'
            }
        }

        stage('Logs') {
            steps {
                sh 'docker logs --tail 50 devops-demo-container'
            }
        }
    }
}
