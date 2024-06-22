pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    def app = docker.build("flask-app")
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    docker.image('flask-app').inside {
                        sh 'echo "No tests available."'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    withKubeConfig([credentialsId: 'kubeconfig']) {
                        sh 'kubectl apply -f k8s/deployment.yaml'
                        sh 'kubectl apply -f k8s/service.yaml'
                    }
                }
            }
        }
    }
}
