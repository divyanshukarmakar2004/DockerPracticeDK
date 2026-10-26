pipeline {
    agent any

    environment {
        IMAGE_NAME = 'my-project-app'
        IMAGE_TAG = 'latest'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub...'
            }
        }

        stage('Verify Environment') {
            steps {
                // Use 'sh' for Linux/Unix environments
                sh 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Use 'sh' for Linux/Unix environments
                sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
            }
        }

        stage('Smoke Test & Health Check') {
            steps {
                // Use 'sh' for Linux/Unix environments
                sh "docker run --rm ${IMAGE_NAME}:${IMAGE_TAG} python --version"
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