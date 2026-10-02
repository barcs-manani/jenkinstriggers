def COLOR_MAP = [
    'SUCCESS': 'good',
    'FAILURE': 'danger',
]
pipeline{
    agent any
    stages{
        stage("Build"){
            steps{
                sh 'echo "Build completed."'
            }
        }
    }
    post{
        always{
            echo "========Notifying on Slack========"
            slackSend channel: '#devops-cicd-learning',
                color: COLOR_MAP[currentBuild.currentResult],
                message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_ID} \n More Info at: ${BUILD_URL}"
        }
    }
}