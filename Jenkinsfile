pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Building the code..."
                sh 'mvn clean package'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit and integration tests..."
                sh 'mvn test'
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo "Analyzing the code..."
                sh 'mvn sonar:sonar'
            }
        }
        
        stage('Security Scan') {
            steps {
                echo "Performing security scan..."
                sh './dependency-check.sh'
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to staging environment..."
                // Add deployment commands here
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging..."
                // Add integration test commands here
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo "Deploying to production environment..."
                // Add deployment commands here
            }
        }
    }
    
    post {
        always {
            echo "Cleaning up workspace..."
            cleanWs()
        }
        
        success {
            mail to: "aniraj2020@gmail.com",
                subject: "Pipeline executed Successfully",
                body: "The Jenkins pipeline has completed successfully."
        }
        
        failure {
            mail to: "aniraj2020@gmail.com",
                subject: "Pipeline execution Failed",
                body: "The Jenkins pipeline has failed. Please check the logs."
        }
    }
}
