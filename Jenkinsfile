
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
def blocks = [
	[
		type: "section",
		text: [
			type: "mrkdwn",
			text: "Hello, Assistant to the Regional Manager Dwight! *Michael Scott* wants to know where you'd like to take the Paper Company investors to dinner tonight.\n\n *Please select a restaurant:*"
		]
	]
]
// def attachments = [
//   [
//     color: '#ff0000',
// 	blocks: [
// 		[
// 			type: "section",
// 			text: [
// 				type: "mrkdwn",
// 				text: "Hello, Assistant to the Regional Manager Dwight! *Michael Scott* wants to know where you'd like to take the Paper Company investors to dinner tonight.\n\n *Please select a restaurant:*"
// 			]
// 		]
// 	]
//   ]
// ]

slackSend(channel: "#devops-testing", blocks: blocks)
		
}