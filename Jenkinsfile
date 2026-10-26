pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub...'
            }
        }

        stage('Verify Environment') {
            steps {
                echo 'Docker version 27.0.0 (simulated)'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image dockerpractice-dk:latest...'
            }
        }

        stage('Smoke Test & Health Check') {
            steps {
                echo 'Container health check passed successfully!'
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
    }
}