pipeline {
    agent any
    environment {
        PROD_ENV = "AWS EC2 instance"
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Building the code..."
                echo "Tool: Maven"
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit and integration tests..."
                echo "Tool: JUnit, Maven"
            }

            post {
                success {
                    mail to: "aniraj2020@gmail.com",
                    subject: "Unit and Integration Tests ran Successfully",
                    body: "The Unit and Integration Tests have been completed successfully."
                }
                failure {
                    mail to: "aniraj2020@gmail.com",
                    subject: "Unit and Integration Tests Failed",
                    body: "The Unit and Integration Tests have failed. Please check the logs."
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo "Analyzing the code..."
                echo "Tool: SonarQube"
            }
        }
        
        stage('Security Scan'){
            steps{
                echo "Perform a security scan to identify vulnerabilities"
                echo "Tool: OWASP Dependency-Check"
            }

            post {
                success {
                    mail to: "aniraj2020@gmail.com",
                    subject: "Security Scan completely Successfully",
                    body: "The Security Scan has been completed successfully."
                }
                failure {
                    mail to: "aniraj2020@gmail.com",
                    subject: "Security Scan has Failed",
                    body: "The Security Scan has failed. Please check the logs."
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to staging environment..."
                echo "Tool: AWS CLI
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging..."
                echo "Tool: Selenium, Postman"
            }

            post {
                success {
                    mail to: "aniraj2020@gmail.com",
                    subject: "Integration Tests on Staging ran Successfully",
                    body: "The Integration Tests on Staging have been completed successfully."
                }
                failure {
                    mail to: "aniraj2020@gmail.com",
                    subject: "Integration Tests on Staging Failed",
                    body: "The Integration Tests on Staging have failed. Please check the logs."
                }
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo "Deploying to production environment: ${env.PROD_ENV}..."
                echo "Tool: Docker"
            }
        }
    }
    
    post {
        success {
            mail to: "aniraj2020@gmail.com",
            subject: "Pipeline executed Successfully",
            body: "The Jenkins pipeline has been completed successfully."
        }
    
        failure {
            mail to: "aniraj2020@gmail.com",
            subject: "Pipeline execution Failed",
            body: "The Jenkins pipeline has failed. Please check the logs."
        }
    }
}
