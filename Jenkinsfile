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
                  cat Jenkinsfile
                  docker images
                '''
            }
        }
        stage('Build') {
            steps {
                script {
                    def dockerImage = docker.build(registry + ":${env.BUILD_ID}")
                    docker.withRegistry( '', registryCredential ) {
                        dockerImage.push()
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }
}
