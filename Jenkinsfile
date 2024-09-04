pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                // Example: sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code...'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
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
