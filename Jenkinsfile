import groovy.json.JsonSlurper

pipeline {
	agent any
	stages {
		stage ('SCM Checkout') {
			steps {
				sh 'echo scm'
			}
		}
		stage ('Build Application') {
			steps {
				sh 'echo build'
			}
		}
		stage ('Deploy Application') {
			steps {
				sh 'echo deploy'
			}
		}
	}
	
	post {
		always {
			script {
				CONSOLE_LOG = "${env.BUILD_URL}/console"
				BUILD_STATUS = currentBuild.currentResult
	
				sh 'echo slack'
				sendSlackNotifcation()
			}
		}
	}
}

def sendSlackNotifcation() 
{ 
	def attachments = """[ {\"type\": \"header\", \"text\": {\"type\": \"plain_text\", \"text\": \"Alert Processing Completed\", \"emoji\": True}} ]"""
        echo (attachments)
        slackSend (channel: "#devops-testing", color: "danger",  blocks: attachments)
		
}