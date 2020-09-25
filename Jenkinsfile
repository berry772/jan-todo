pipeline {
    environment {
        registry = "berry772/todo-jenkins"
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
        stage('Build') {
            steps {
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
    }
}
