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
                script {
                    echo 'Running unit tests using Jest'
                    echo 'Running integration tests using Jest'
                }
            }
           post {
                always {
                    echo 'Sending notification email to ${EMAIL}...'
                    sh "touch logs.txt"
                    echo 'Attaching logs.txt...'
                }
                success {
                    echo "Status: SUCCESS"
                    emailext (
                    to: "auanson2918@gmail.com",
                    subject: "Unit and Integration Test Status",
                    body: "Test was successful!",
                    from: "nobody@nowhere",
                    attachmentsPattern: '**/logs.txt' 
                    )
                }
               failure {
                    echo "Status: FAILURE"
                    emailext (
                    to: "auanson2918@gmail.com",
                    subject: "Unit and Integration Test Status",
                    body: "Test failed!",
                    from: "nobody@nowhere",
                    attachmentsPattern: '**/logs.txt' 
                    )
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
                script {
                    echo 'Performing security scan using OWASP ZAP'
                    sh 'echo "Security Scan log content" > security_scan.log'
                }
            }
          post {
                always {
                    echo 'Sending notification email to ${EMAIL}...'
                    sh "touch logs.txt"
                    echo 'Attaching logs.txt...'
                }
                success {
                    echo "Status: SUCCESS"
                    emailext (
                    to: "auanson2918@gmail.com",
                    subject: "Security Scan Status",
                    body: "Scan was successful!",
                    from: "nobody@nowhere",
                    attachmentsPattern: '**/logs.txt' 
                    )
                }
               failure {
                    echo "Status: FAILURE"
                    emailext (
                    to: "auanson2918@gmail.com",
                    subject: "Security Scan Status",
                    body: "Scan failed!",
                    from: "nobody@nowhere",
                    attachmentsPattern: '**/logs.txt' 
                    )
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
        stage('Completed') {
            steps {
                echo 'Project Completed'
            }
        }
    }
}

