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
        script {
	    def jobName = env.JOB_NAME
	    def buildNumber = env.BUILD_NUMBER
            def pipelineStatus = currentBuild.result ?: 'UNKNOWN'
	    def bannerColor = pipelineStatus.toUpperCase() == 'SUCCESS' ? 'green' : 'red'

	    def body = """<html>
			     <body>
				 <div style="border: 4px solid ${bannerColor}; padding:10px;">
				       <h2>${jobName} - Build ${buildNumber}</h2>
				       <div style="background-colour: ${bannerColor}; padding: 10px;">
					    <h3 style="color: white;">Pipeline Status:
					    ${pipelineStatus.toUpperCase()}</h3>
				       </div>
				       <p>Check the <a href="${BUILD_URL}">console.output</a>.</p>
				 </div>
			     </body>
			  </html>"""
	    emailext (
		subject: "${jobName} - Build ${buildNumber} - ${pipelineStatus.toUpperCase()}",
		body: body,
		to: 'priyanshu110603@gmail.com',
		from: 'jenkins@example.com',
		replyTo: 'jenkins@example.com',
		mimeType: 'text/html'  
    }
}
