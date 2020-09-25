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
                '''
            }
        }
        stage('Cloning Git') {
            steps {
                git 'https://github.com/berry772/jan-todo.git'
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
