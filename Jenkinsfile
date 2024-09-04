pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit and integration tests...'
                    try {
                        // Example: sh 'mvn test'
                    } catch (Exception e) {
                        currentBuild.result = 'FAILURE'
                        throw e
                    }
                }
            }
            post {
                always {
                    script {
                        emailext(
                            to: 'priyanshu110603@gmail.com',
                            subject: "Unit and Integration Tests ${currentBuild.result}: ${currentBuild.fullDisplayName}",
                            body: "The Unit and Integration Tests stage has ${currentBuild.result}. Check the attached logs for details.",
                            attachmentsPattern: 'test-results/*.xml'
                        )
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code...'
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo 'Performing security scan...'
                    try {
                        // Example: sh 'security-scan.sh'
                    } catch (Exception e) {
                        currentBuild.result = 'FAILURE'
                        throw e
                    }
                }
            }
            post {
                always {
                    script {
                        emailext(
                            to: 'priyanshu110603@gmail.com',
                            subject: "Security Scan ${currentBuild.result}: ${currentBuild.fullDisplayName}",
                            body: "The Security Scan stage has ${currentBuild.result}. Check the attached logs for details.",
                            attachmentsPattern: 'security-scan-logs/*.log'
                        )
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
            }
        }
    }

    post {
        always {
            echo 'Pipeline complete.'
        }
        success {
            emailext to: 'priyanshu110603@gmail.com',
                     subject: "Pipeline Successful: ${currentBuild.fullDisplayName}",
                     body: "The Jenkins Pipeline has completed successfully."
        }
        failure {
            emailext to: 'priyanshu110603@gmail.com',
                     subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                     body: "The Jenkins Pipeline has failed."
        }
    }
}

