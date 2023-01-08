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
                }                
            }
        }

        stage ('Push Image') {
            environment {
                tag_version = "${env.BUILD_ID}"
            }            
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PWD')]) {
                        sh 'docker login -u $DOCKER_USER -p $DOCKER_PWD'
                        sh 'docker push fabricioveronez/kube-news:$tag_version'
                        sh 'docker push fabricioveronez/kube-news:latest'
                    }
                }
            }
        }

        // stage('Deploy Kubernetes') {
        //     environment {
        //         tag_version = "${env.BUILD_ID}"
        //     }
        //     steps {
        //         withKubeConfig([credentialsId: 'kubeconfig']) {
        //             sh 'sed -i "s/{{tag}}/$tag_version/g" ./k8s/deployment.yaml'
        //             sh 'kubectl apply -f ./k8s/deployment.yaml'                    
        //         }
        //     }
        // }
    }
}
