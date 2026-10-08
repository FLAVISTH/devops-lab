pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t devops-lab-app:latest .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker stop devops-lab-container || true
                    docker rm devops-lab-container || true
                    docker run -d --name devops-lab-container -p 8080:80 devops-lab-app:latest
                '''
            }
        }
    }
}
