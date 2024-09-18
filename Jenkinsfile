pipeline {
    agent any
    
    
    stages {
        stage('Stage 1: Build') {
            steps {
                echo 'Tool: Maven - Used to compile, package, and build the application.'
            }
        }
        
        stage('Stage 2: Unit and Integration Tests') {
            steps {
                echo 'Tools: JUnit for unit testing and TestNG for integration testing.'
            }
            post {
                always {
                    emailext (
                        to: "themindauvin@gmail.com",
                        subject: "Unit and Integration Test Results",
                        body: "Unit and Integration Tests have completed",
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        to: "themindauvin@gmail.com",
                        subject: "Unit and Integration Tests Failed",
                        body: "The tests failed. Check the attached logs for details.",
                        attachLog: true
                    )
                }
            }
        }


        stage('Stage 3: Code Analysis') {
            steps {
                echo 'Tool: SonarQube - Used to perform static code analysis to detect code quality issues.'
            }
        }
    
        stage('Stage 4: Security Scan') {
            steps {
                echo 'Tool: OWASP Dependency-Check - Used to identify vulnerabilities in project dependencies.'
            }
            post {
                success {
                    mail to: "themindauvin@gmail.com",
                    subject: "Security scan",
                    body: "The security scan succeeded"
                }
                
            }
        }
    
        stage('Stage 5: Deploy to Staging') {
            steps {
                echo 'Tool: SCP or AWS CLI - Used to deploy the application to an AWS EC2 instance.'
            }
        }
    
        stage('Stage 6: Integration Tests on Staging') {
            steps {
                echo 'Tool: Custom integration test scripts or tools like Postman or Selenium for API and UI testing.'
            }
        }
    
        stage('Stage 7: Deploy to Production') {
            steps {
                echo 'Tool: SCP or AWS CLI - Used to deploy the application to a production AWS EC2 instance.'
            }
        }
    }
}
