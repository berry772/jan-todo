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
                  docker images
                '''
            }
        }
        stage('Build') {
            steps {
                script {
                    def dockerImage = docker.build(registry + ":${env.BUILD_ID}")
                    dockerImage.push()
                    dockerImage.push('latest')
                }
            }
        }
    }
}
