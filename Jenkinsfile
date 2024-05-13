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
                always {
                    mail to: "auanson2918@gmail.com", 
                    subject: "Unit and Integration Tests Passed",
                    body: "Unit and Integration Tests log attached!"
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
                always {
                    mail to: "auanson2918@gmail.com",
                    subject: "Security Scan Passed",
                    body: "Security Scan log attached!"
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