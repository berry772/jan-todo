pipeline {
    environment {
        registry = 'berry772/jan-todo-a'
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
                    def dockerImage = docker.build(registry + ":${env.BUILD_ID}")
                    docker.withRegistry( '', registryCredential ) {
                        dockerImage.push()
                        dockerImage.push('latest')
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    aws.withRegistry('','aws') {
                        echo 'tttttttttttttttttttttttt'
                    }
                }
            }
        }
    }
}
