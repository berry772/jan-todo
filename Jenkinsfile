pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh '''
                  ls -la
                  cat Dockerfile
                  docker images
                '''
                script {
                    checkout scm
                    def customImage = docker.build("${registry}${BUILD_NUMBER}:${env.BUILD_ID}")
                    customImage.push()
                }
            }
        }
    }
}
