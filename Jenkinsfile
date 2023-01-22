pipeline {
    agent any

    stages {
        stage ('Build Image') {
            steps {
                script {
                    sh 'echo "Construir a imagem docker"'
                }                
            }
        }

        stage ('Push Image') {    
            steps {
                script {
                    sh 'echo "Subir imagem de container"'
                }                
            }
        }

        stage ('Deploy Kubernetes') {
            steps {
                script {
                    sh 'echo "Deploy no Kubernetes"'
                }                
            }
        }
    }
}
