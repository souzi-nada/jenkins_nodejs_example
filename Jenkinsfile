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
                sh 'docker build . -f dockerfile -t ${USER}/nodejs-iamge:v1.${BUILD_NUMBER}'
                sh 'docker login -u ${USER} -p ${PASS}'
                sh 'docker push ${USER}/nodejs-iamge:v1.${BUILD_NUMBER}'
                }
            }
        }
    
        stage('deploy') {
            steps {
                withCredentials([usernamePassword(credentialsId:"docker",usernameVariable:"USER",passwordVariable:"PASS")]){
                sh 'docker run -d -p 3000:3000 ${USER}/nodejs-iamge:v1.${BUILD_NUMBER}'
                }
            }
        }
    }
}
