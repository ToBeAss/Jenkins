pipeline {
    agent any
    environment {
        EMAIL="mollandtobias@gmail.com"
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
                    echo "Attaching logs.txt..."
                }
                success {
                    echo "Status: SUCCESS"
                    emailext (
                        subject: "Unit and Integration Test Status",
                        body: "Tests were successful!",
                        to: "${EMAIL}",
                        from: "nobody@nowhere",
                        attachLog: true
                    )
                }
                failure {
                    echo "Status: FAILURE"
                    emailext (
                        subject: "Unit and Integration Test Status",
                        body: "Tests failed!",
                        to: "${EMAIL}",
                        from: "nobody@nowhere",
                        attachLog: true
                    )
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
                    sh "touch logs.txt"
                    echo "Attaching logs.txt..."
                }
                success {
                    echo "Status: SUCCESS"
                    emailext (
                        subject: "Security Scan Status",
                        body: "Scans were successful!",
                        to: "${EMAIL}",
                        from: "nobody@nowhere",
                        attachLog: true
                    )
                }
                failure {
                    echo "Status: FAILURE"
                    emailext (
                        subject: "Security Scan Status",
                        body: "Scans failed!",
                        to: "${EMAIL}",
                        from: "nobody@nowhere",
                        attachLog: true
                    )
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
                    sh "touch logs.txt"
                    echo "Attaching logs.txt..."
                }
                success {
                    echo "Status: SUCCESS"
                    emailext (
                        subject: "Integration Test Status",
                        body: "Tests were successful!",
                        to: "${EMAIL}",
                        from: "nobody@nowhere",
                        attachLog: true
                    )
                }
                failure {
                    echo "Status: FAILURE"
                    emailext (
                        subject: "Integration Test Status",
                        body: "Tests failed!",
                        to: "${EMAIL}",
                        from: "nobody@nowhere",
                        attachLog: true
                    )
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