pipeline {
    agent any
    environment {
        PROD_ENV = "AWS EC2 instance"
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Building the code..."
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit and integration tests..."
            }

            post {
                success {
                    emailext (
                        to: "aniraj2020@gmail.com",
                        subject: "Unit and Integration Tests ran Successfully",
                        body: "The Unit and Integration Tests have been completed successfully.",
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        to: "aniraj2020@gmail.com",
                        subject: "Unit and Integration Tests Failed",
                        body: "The Unit and Integration Tests have failed. Please check the attached logs.",
                        attachLog: true
                    )
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo "Analyzing the code..."
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to staging environment..."
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging..."
            }

            post {
                success {
                    emailext (
                        to: "aniraj2020@gmail.com",
                        subject: "Integration Tests on Staging ran Successfully",
                        body: "The Integration Tests on Staging have been completed successfully.",
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        to: "aniraj2020@gmail.com",
                        subject: "Integration Tests on Staging Failed",
                        body: "The Integration Tests on Staging have failed. Please check the attached logs.",
                        attachLog: true
                    )
                }
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo "Deploying to production environment: ${env.PROD_ENV}..."
            }
        }
    }
    
    post {
        success {
            emailext (
                to: "aniraj2020@gmail.com",
                subject: "Pipeline executed Successfully",
                body: "The Jenkins pipeline has completed successfully.",
                attachLog: true
            )
        }
    
        failure {
            emailext (
                to: "aniraj2020@gmail.com",
                subject: "Pipeline execution Failed",
                body: "The Jenkins pipeline has failed. Please check the attached logs.",
                attachLog: true
            )
        }
    }
}
