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
                echo "Run unit tests to ensure the code functions as expected and run integration tests to ensure the different components of the application work together as expected"
                echo "Running tests with Appium..."
            }
            post {
                always {
                    echo "Sending notification email to ${EMAIL}..."
                    sh "touch logs.txt"
                    sh "mail -s 'Unit and Integration Tests' -A logs.txt ${EMAIL}"
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
                echo "Analysing code with Coverity..."
            }
        }
        stage('Security Scan') {
            steps {
                echo "Perform a security scan on the code using a tool to identify any vulnerabilities"
                echo "Scanning code for vulnerabilities with Nessus..."
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
        stage('Deploy to Staging') {
            steps {
                echo "Deploy the application to a staging server"
                echo "Deploying to AWS EC2 staging instance..."
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Run integration tests on the staging environment to ensure the application functions as expected in a production-like environment"
                echo "Running integration tests in staging environment with Appium..."
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
        stage('Deploy to Production') {
            steps {
                echo "Deploy the application to a production server"
                echo "Deploying to AWS EC2 production instance..."
            }
        }
    }
}