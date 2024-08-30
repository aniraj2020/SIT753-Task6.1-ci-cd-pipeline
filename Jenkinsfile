pipeline {
    agent any
    environment {
        PROD_ENV = "AWS EC2 instance"
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Let's go...again"
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
                    emailext(
                        to: "aniraj2020@gmail.com",
                        subject: "SUCCESS: Unit and Integration Tests",
                        body: "The Unit and Integration Tests have been completed successfully.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "aniraj2020@gmail.com",
                        subject: "FAILURE: Unit and Integration Tests",
                        body: "The Unit and Integration Tests have failed. Please check the attached logs.",
                        attachLog: true
                    )
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo "Analyzing the code..."
                echo "Tool: SonarQube"
            }
        }
        
        stage('Security Scan') {
            steps {
                echo "Performing a security scan to identify vulnerabilities"
                echo "Tool: OWASP Dependency-Check"
            }

            post {
                success {
                    emailext(
                        to: "aniraj2020@gmail.com",
                        subject: "SUCCESS: Security Scan",
                        body: "The Security Scan has been completed successfully.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "aniraj2020@gmail.com",
                        subject: "FAILURE: Security Scan",
                        body: "The Security Scan has failed. Please check the attached logs.",
                        attachLog: true
                    )
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to staging environment..."
                echo "Tool: AWS CLI"
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging..."
                echo "Tool: Selenium, Postman"
            }

            post {
                success {
                    emailext(
                        to: "aniraj2020@gmail.com",
                        subject: "SUCCESS: Integration Tests on Staging",
                        body: "The Integration Tests on Staging have been completed successfully.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "aniraj2020@gmail.com",
                        subject: "FAILURE: Integration Tests on Staging",
                        body: "The Integration Tests on Staging have failed. Please check the attached logs.",
                        attachLog: true
                    )
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
            emailext(
                to: "aniraj2020@gmail.com",
                subject: "SUCCESS: Pipeline executed",
                body: "The Jenkins pipeline has been completed successfully.",
                attachLog: true
            )
        }
    
        failure {
            emailext(
                to: "aniraj2020@gmail.com",
                subject: "FAILURE: Pipeline execution",
                body: "The Jenkins pipeline has failed. Please check the attached logs.",
                attachLog: true
            )
        }
    }
}
