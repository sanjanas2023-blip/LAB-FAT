pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Builds the Docker image from the Dockerfile
                sh 'docker build -t university-web:latest .'
            }
        }
        stage('Test') {
            steps {
                // Validates that Nginx starts correctly
                sh 'docker run --rm university-web:latest nginx -t'
            }
        }
        stage('Deploy') {
            steps {
                // Applies the Kubernetes configuration to Docker Desktop
                sh 'kubectl apply -f deployment.yaml'
            }
        }
    }
}
