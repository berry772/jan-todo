pipeline {
  agent none
  node {
    stages {
    stage('Test') {
      steps {
        sh '''
            ls -la
            cat Dockerfile
        '''
      }
    }
    stage('Building Image') {
      steps {
        sh '''
            pwd
            ls -la
            docker ps -a
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
  environment {
    registry = 'berry772/jan-todo'
  }
}
