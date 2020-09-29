pipeline {
    environment {
        registry = 'berry772/jan-todo-a'
        registryCredential = 'dockerhub'
        AWS_ID = credentials('aws')
        AWS_ACCESS_KEY_ID = "${env.AWS_ID_USR}"
        AWS_SECRET_ACCESS_KEY = "${env.AWS_ID_PSW}"
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
                    /* docker.withRegistry( '', registryCredential ) {
                        dockerImage.push()
                        dockerImage.push('latest')
                    } */
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    echo '${env.AWS_ACCESS_KEY_ID}'
                }
            }
        }
    }
}
