pipeline {
    agent any

    stages {
        stage('prep') {
            steps {
                git 'https://github.com/souzi-nada/jenkins_nodejs_example.git'
            }
        }
        stage('build') {
            steps {
             //   withCredentials([usernamePassword(credentialsId:"docker",usernameVariable:"USER",passwordVariable:"PASS")]){
             //   sh 'docker build . -f dockerfile -t ${USER}/nodejs-iamge-yat225:v1.${BUILD_NUMBER}'
             //  sh 'docker login -u ${USER} -p ${PASS}'
             //   sh 'docker push ${USER}/nodejs-iamge-yat225:v1.${BUILD_NUMBER}'
             //   sh 'docker rm -f live'
             //   sh 'docker run -d -p 3000:3000 --name live ${USER}/nodejs-iamge-yat225:v1.${BUILD_NUMBER}'
             //   }
            }
        }
    }
    // post {
    //     success {
    //         withCredentials([usernamePassword(credentialsId:"docker",usernameVariable:"USER",passwordVariable:"PASS")]){
    //             sh 'docker login -u ${USER} -p ${PASS}'
    //             sh 'docker push ${USER}/nodejs-iamge:v1.${BUILD_NUMBER}'
    //             slackSend(
    //             channel: "devops",
    //             color: "good",
    //             message: "${env.JOB_NAME} is successeded. Build no. ${env.BUILD_NUMBER} (<https://hub.docker.com/repository/docker/${USER}/nodejs-iamge/general|Open the image link>)"
    //         )
    //             sh 'docker rm -f $(docker ps -aq)'
    //             sh 'docker run -d -p 3000:3000 ${USER}/nodejs-iamge:v1.${BUILD_NUMBER}'
    //         }
    //     }
    //     failure {
    //         slackSend(
    //             channel: "devops",
    //             color: "danger",
    //             message: "${env.JOB_NAME} is failed. Build no. ${env.BUILD_NUMBER} URL: ${env.BUILD_URL} (<${env.BUILD_URL}|Open the pipeline>)"
    //         )
    //     }
    // }
}
