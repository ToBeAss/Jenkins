pipeline {
    agent any
    environment {
        EMAIL="s224289859@deakin.edu.au"
    }

    stages {
        stage('Delay') {
            steps {
                sleep 5
            }
        }
        stage('Build') {
            steps {
                echo "Build the code using a build automation tool to compile and package your code"
                echo "Building code with Maven..."
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "run unit tests to ensure the code functions as expected and run integration tests to ensure the different components of the application work together as expected"
            }
            post {
                always {
                    echo "Sending notification email to ${EMAIL}..."
                }
                success {
                    echo "Status: SUCCESS"
                }
                failure {
                    echo "Status: FAILURE"
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Integrate a code analysis tool to analyse the code and ensure it meets industry standards"
            }
        }
        stage('Security Scan') {
            steps {
                echo "perform a security scan on the code using a tool to identify any vulnerabilities"
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "deploy the application to a staging server"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "run integration tests on the staging environment to ensure the application functions as expected in a production-like environment"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "deploy the application to a production server"
            }
        }
    }
}