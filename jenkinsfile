pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building the code using Maven"
                sleep(time: 1, unit: 'SECONDS')
                echo "Build Successful"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit and integration tests using JUnit (for unit tests), Selenium (for integration tests)..."
                sleep(time: 1, unit: 'SECONDS')
                echo "Build Successful"
            }
            post {
                success {
                    emailext (
                        attachLog: true, 
                        body: 'Stage completed successfully. Logs are attached.', 
                        subject: 'Stage Success: Security Scan', 
                        to: 'matthew.sutrisno03@gmail.com'
                    )
                }
                failure {
                    emailext (
                        to: 'matthew.sutrisno03@gmail.com',
                        subject: "Stage Failed: Unit and Integration Tests",
                        body: "Stage failed. Logs are attached.",
                        attachLog: true
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Analyzing code using SonarQube..."
                sleep(time: 1, unit: 'SECONDS')
                echo "Analyzing Successful"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Performing security scan using OWASP ZAP"
                sleep(time: 1, unit: 'SECONDS')
                echo "Scan Successful"
            }
            post {
                success {
                    emailext (
                        attachLog: true, 
                        body: 'Stage completed successfully. Logs are attached.', 
                        subject: 'Stage Success: Security Scan', 
                        to: 'matthew.sutrisno03@gmail.com'
                    )
                }
                failure {
                    emailext (
                        to: 'matthew.sutrisno03@gmail.com',
                        subject: "Stage Failed: Security Scan",
                        body: "Stage failed. Logs are attached.",
                        attachLog: true
                    )
                }
            }
        }
        stage('Deploying to Staging') {
            steps {
                echo "Deploying to staging server in Jenkins"
                sleep(time: 1, unit: 'SECONDS')
                echo "Deploying Successful"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment using Selenium'
                sleep(time: 1, unit: 'SECONDS')
                echo "Testing Successful"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying to production server"
                sleep(time: 1, unit: 'SECONDS')
                echo "Deploying Successful"
            }
        }
    }
}
