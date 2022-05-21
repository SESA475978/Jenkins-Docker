pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('9739140003')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/SESA475978/Jenkins-Docker.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t 9739140003/nodeapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push 9739140003/nodeapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}

