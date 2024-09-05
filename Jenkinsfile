pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                // Example: sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using JUnit...'
                // Example: sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with SonarQube...'
                // Example: sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan with OWASP Dependency-Check...'
                // Example: sh 'dependency-check.sh --project JenkinsPipelineDemo'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                // Example: sh 'scp target/app.war user@staging-server:/var/www/app/'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
                // Example: sh 'curl -s http://staging-server/app/test'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                // Example: sh 'scp target/app.war user@production-server:/var/www/app/'
            }
        }
    }

    post {
        always {
            echo 'Pipeline complete.'
        }
        success {
            mail to: 'priyanshu110603@gmail.com',
                subject: "Pipeline Successful: ${currentBuild.fullDisplayName}",
                body: "The Jenkins Pipeline has completed successfully.",
                attachLog: true
        }
        failure {
            mail to: 'priyanshu110603@gmail.com',
                subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                body: "The Jenkins Pipeline has failed.",
                attachLog: true
        }
    }
}
