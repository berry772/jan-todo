pipeline {
    environment {
        registry = "berry772/jan-todo"
    }
    agent {
        docker { image 'node:12-alpine' }
    }
    stages {
        stage('Test') {
            steps {
                sh '''
                    node --version
                    echo "Hello from stage test"
                    ls -la
                '''
            }
        }
        stage('Building Image') {
            steps {
                sh '''
                    ls -la
                    cat Dockerfile
                    docker ps -a
                '''
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
    }
}
