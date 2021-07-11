pipeline {
    agent any

    environment {
        registryCredentials = 'dockerhubcredentials'
    }
    stages {
        stage('Docker Build') {
            steps {
                script {
                    dockerImage = docker.build(appTag, ".")
                }                
            }
        }
        stage('Docker Push') {
            steps {
                script {
                    docker.withRegistry('', registryCredentials) {
                        dockerImage.push()
                    }                        
                }
            }            
        }
        stage('Docker Run') {
            steps {                
                sh "docker run -d -p ${appPort}:80  ${appTag}"
            }
        }        
    }
}