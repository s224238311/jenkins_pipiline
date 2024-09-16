pipeline {
    agent any
    tools{
        maven 'Maven 3.9.9'
    }
    
    stages {
        stage('Stage 1: Build') {
            steps {
                echo 'Tool: Maven - Used to compile, package, and build the application.'
            }
        }

        stage('Stage 2: Unit and Integration Tests') {
            steps {
                echo 'Tools: JUnit for unit testing and TestNG for integration testing.'
                // Capture both standard output and error output into the log file
                bat 'mvn test -X > unit_test.log 2>&1' // Run Maven tests with debug logging and capture errors
                archiveArtifacts artifacts: 'unit_test.log', allowEmptyArchive: true
                bat 'type unit_test.log' // Print the log to the console for debugging
            }
            post {
                success {
                    emailext (
                        to: "themindauvin@gmail.com",
                        subject: "Unit test and Integration test succeeded",
                        body: """Unit test and Integration test succeeded. 
                        Please find the logs attached.""",
                        attachmentsPattern: "unit_test.log",
                        mimeType: 'text/plain'
                    )
                }
                failure {
                    script {
                        echo "Unit test and Integration test failed. Printing the log:"
                        bat 'type unit_test.log' // Print the log in case of failure
                        emailext (
                            to: "themindauvin@gmail.com",
                            subject: "Unit test and Integration test failed",
                            body: """Unit test and Integration test failed. 
                            Please find the logs attached.""",
                            attachmentsPattern: "unit_test.log",
                            mimeType: 'text/plain'
                        )
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
