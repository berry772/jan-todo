pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh '''
                  ls -la
                  cat Dockerfile
                  docker ps
                '''
            }
        }
    }
}
