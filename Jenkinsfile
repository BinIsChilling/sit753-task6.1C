pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests using Jest'
                echo 'Running integration tests using Jest'
            }
            post {
                success {
                    emailext subject: 'Unit and Integration Tests Passed',
                              body: 'Unit and Integration Tests passed successfully.',
                              attachmentsPattern: '**/target/surefire-reports/*.txt'
                }
                failure {
                    emailext subject: 'Unit and Integration Tests Failed',
                              body: 'Unit and Integration Tests failed.',
                              attachmentsPattern: '**/target/surefire-reports/*.txt'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing the code using SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP ZAP'
            }
            post {
                success {
                    emailext subject: 'Security Scan Passed',
                              body: 'Security Scan passed successfully.',
                              attachmentsPattern: '**/security-scan-results/*.txt'
                }
                failure {
                    emailext subject: 'Security Scan Failed',
                              body: 'Security Scan failed.',
                              attachmentsPattern: '**/security-scan-results/*.txt'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server using AWS EC2 instance'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server using AWS EC2 instance'
            }
        }
    }
}


