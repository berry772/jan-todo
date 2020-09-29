pipeline {
    environment {
        registry = 'berry772/jan-todo'
        registryCredential = 'dockerhub-t'
    }
    agent any
    stages {
        stage('Test') {
            steps {
                sh '''
                  ls -la
                  cat Jenkinsfile
                  docker images
                '''
            }
        }
        stage('Build') {
            steps {
                script {
                    def dockerImage = docker.build(registry + "-a:${env.BUILD_ID}")
                    docker.withRegistry( '', registryCredential ) {
                        dockerImage.push()
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }
}
