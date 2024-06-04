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
                    sh 'echo "Unit and Integration Tests log content" > unit_integration_tests.log'
                }
            }
            post {
                always {
                    archiveArtifacts artifacts: 'unit_integration_tests.log', allowEmptyArchive: true
                        mail to: "auanson2918@gmail.com",
                        subject: "Unit and Integration Tests ${currentBuild.currentResult}",
                        body: """<p>Unit and Integration Tests have completed with status: ${currentBuild.currentResult}.</p>
                                 <p>Find the attached logs for more details.</p>""",
                        attachLog: true,
                        attachmentsPattern: 'unit_integration_tests.log'
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
                    archiveArtifacts artifacts: 'security_scan.log', allowEmptyArchive: true
                        mail to: "auanson2918@gmail.com",
                        subject: "Security Scan ${currentBuild.currentResult}",
                        body: """<p>Security Scan has completed with status: ${currentBuild.currentResult}.</p>
                                 <p>Find the attached logs for more details.</p>""",
                        attachLog: true,
                        attachmentsPattern: 'security_scan.log'
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
