pipeline {
  agent {
    dockerfile true
  }
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
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }

      }
    }

  }
  environment {
    registry = 'berry772/jan-todo'
  }
}