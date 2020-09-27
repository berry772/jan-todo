pipeline {
    environment {
        registry = "berry772/jan-todo"
    }
    agent { dockerfile true }
    stages {
        stage('Test') {
            steps {
                sh '''
                    ls -la
                    cat Dockerfile
                    docker ps -a
                '''
            }
        }
        stage('Building Image') {
            steps {
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
    }
}
