pipeline {
    agent {
        label 'aws-agent'
    }

    stages {
        stage ('build') {
            steps{
                script{
                    sh 'mvn clean package'
                }
            }
        }

        stage ('test') {
            steps{
                script{
                    echo 'test in progress'
                }
            }
        }
    }
    
    post {
        success {
            slackSend channel: '#jenkins-ci', message: 'Build Started - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)', teamDomain: 'devops-rza6966', tokenCredentialId: 'Slack-Bot-Token'
        }
    }

    post {
        failure {
            slackSend channel: '#jenkins-ci', message: 'Build Failed - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)', teamDomain: 'devops-rza6966', tokenCredentialId: 'Slack-Bot-Token'
        }
    }

}



