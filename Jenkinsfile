pipeline {
    agent {
        docker { image 'node:12-alpine' }
    }
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
