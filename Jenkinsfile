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
                success {
                    emailtext {
                        subject: "Jenkins Pipeline: Unit and Integration test passed",
                        body: "The unit and integration test stage is completed successfully",
                        to: 'themindauvin@gmail.com'
                        attachLog: true
                    }
                }
                failure {
                    emailtext {
                        subject: "Jenkins Pipeline: Unit and Integration test failed",
                        body: "The unit and integration test stage has failed",
                        to: 'themindauvin@gmail.com'
                        attachLog: true
                    }
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
                    emailtext {
                        subject: "Jenkins Pipeline: Security scan passed",
                        body: "The security scan stage is completed successfully",
                        to: 'themindauvin@gmail.com'
                        attachLog: true
                    }
                }
                failure {
                    emailtext {
                        subject: "Jenkins Pipeline: Security scan failed",
                        body: "The Security scan stage has failed",
                        to: 'themindauvin@gmail.com'
                        attachLog: true
                    }
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
