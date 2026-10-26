pipeline {
    agent any

    environment {
        IMAGE_NAME = 'my-project-app'
        IMAGE_TAG = 'latest'
    }

    stages {
        stage('Checkout') {
            steps {
                // SCM checkout step
                echo 'Checking out source code from GitHub...'
            }
        }

        stage('Verify Environment') {
            steps {
                // Verify Docker is running on your Windows machine
                bat 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build the image using the local Dockerfile
                bat "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
            }
        }

        stage('Smoke Test & Health Check') {
            steps {
                // Run a temporary container to verify image viability
                bat "docker run --rm ${IMAGE_NAME}:${IMAGE_TAG} python --version"
            }
        }
    }

    post {
        always {
            echo 'Build pipeline completed.'
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Inspect console output for details.'
        }
    }
}