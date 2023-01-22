pipeline {
    agent any

    stages {
				stage ('Build Image') {
            environment {
                tag_version = "${env.BUILD_ID}"
            }
            steps {
                script {
                    sh 'docker build -t fabricioveronez/kube-news:$tag_version -f ./src/Dockerfile ./src'
                    sh 'docker tag fabricioveronez/kube-news:$tag_version fabricioveronez/kube-news:latest'
										sh 'docker image ls'
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
