pipeline {
    agent any

    stages {
        stage('prep') {
            steps {
                git 'https://github.com/IslamReda/jenkins_nodejs_example.git'
            }
        }
        stage('build') {
            steps {
                withCredentials([usernamePassword(credentialsId:"docker",usernameVariable:"USER",passwordVariable:"PASS")]){
                sh 'docker build -f dockerfile -t ${USER}/nodejs-iamge:v1.${BUILD_NUMBER}'
                }
            }
        }
    }
    post {
        success {
            withCredentials([usernamePassword(credentialsId:"docker",usernameVariable:"USER",passwordVariable:"PASS")]){
                sh 'docker login -u ${USER} -p ${PASS}'
                sh 'docker push ${USER}/nodejs-iamge:v1.${BUILD_NUMBER}'
                }
        }
        failure {
            slackSend(
                channel: "devops",
                color: "danger",
                message: "${env.JOB_NAME} is failed. Build no. ${env.BUILD_NUMBER} URL: ${env.BUILD_URL} (<${env.BUILD_URL}|Open the pipeline>)"
            )
        }
    }
}
