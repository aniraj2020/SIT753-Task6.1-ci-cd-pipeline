pipeline {
    agent any
    
    stages {
        stage('Test Email Sending') {
            steps {
                echo "Running a minimal test..."
            }
            post {
                success {
                    emailext(
                        to: "aniraj2020@gmail.com",
                        subject: "SUCCESS: Test Email",
                        body: "This is a test email from a minimal pipeline.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "aniraj2020@gmail.com",
                        subject: "FAILURE: Test Email",
                        body: "This is a test email from a minimal pipeline.",
                        attachLog: true
                    )
                }
            }
        }
    }
}
