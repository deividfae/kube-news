pipeline {
    agent any

    stages {

        stage ('Build Image') {
            steps {
                script {
                    dockerapp = docker.build("deividfae/kube-news:v${env.BUILD_ID}", '-f ./src/Dockerfile ./src') 
                }                
            }
        }

        stage ('Push Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        dockerapp.push('latest')
                        dockerapp.push("v${env.BUILD_ID}")
                    }
                }
            }
        }

    }
}