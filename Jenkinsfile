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
          checkout scm
          def customImage = docker.build("${registry}${BUILD_NUMBER}:${env.BUILD_ID}")
          customImage.push()
        }

      }
    }

  }
  environment {
    registry = 'berry772/jan-todo'
  }
}