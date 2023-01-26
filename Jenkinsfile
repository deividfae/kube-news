pipeline {
    agent any

    stages {

        stage ('Build Image') {
            steps {
                script {
                    // adicionei v na versão para seguir o padrão que foi utilizando nos dias anteriores
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