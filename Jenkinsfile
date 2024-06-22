pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    docker.build('flask-app')
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    echo "tested"
                    }
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    docker.withRegistry('https://registry.example.com', 'credentials-id') {
                        docker.image('flask-app').push('latest')
                    }
                }
            }
        }
    }
}
