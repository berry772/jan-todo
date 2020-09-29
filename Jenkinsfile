pipeline {
    environment {
        registry = 'berry772/jan-todo'
        registryCredential = 'dockerhub'
    }
    agent any
    stages {
        stage('Test') {
            steps {
                sh '''
                  ls -la
                  cat Dockerfile
                  docker image prune -f
                '''
            }
        }
        stage('Build') {
            steps {
                script {
                    def dockerImage = docker.build(registry + "-a:${env.BUILD_ID}")
                    dockerImage.push()
                    dockerImage.push('latest')
                }
            }
        }
    }
}
