pipeline {
    agent any
    tools {
        nodejs 'NodeJS' // Replace with the name configured under Manage Jenkins -> Tools
    }
    
    options {
        skipStagesAfterUnstable()
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'npm test'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                script {
                    if (sh(script: 'which docker', returnStatus: true) == 0) {
                        sh "docker build -t my-cicd-app:${env.BUILD_NUMBER} ."
                    } else {
                        echo 'Docker not available – skipping real image build'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                script {
                    if (sh(script: 'which docker', returnStatus: true) == 0) {
                        sh 'docker stop my-cicd-app || true'
                        sh 'docker rm my-cicd-app || true'
                        sh "docker run -d --name my-cicd-app -p 3001:3000 my-cicd-app:${env.BUILD_NUMBER}"
                    } else {
                        echo 'Simulating deployment (Docker not available)'
                        sh "echo \"Deployed build ${env.BUILD_NUMBER} to server (simulated)\""
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished'
        }
        success {
            echo 'Deployment succeeded'
        }
        failure {
            echo 'Pipeline failed – check logs'
        }
    }
}
