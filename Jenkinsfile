pipeline {
    agent any
    stages {
        stage('Build and Deploy'){
            steps{
                sh './web_demo/build_run.sh'
            }
        }
        stage('Zap') {
            steps {
                sh 'cd zap && ./full_scan.sh'
            }
        }

        stage('Clean Up docker'){
            steps{
                sh './web_demo/stop.sh'
                sh 'cat zap/report.json'
            }
        }
    }
}
