pipeline {
  agent any
  stages {
    stage('aws cred') {
      steps {
        sh '''echo $AWS_PROFILE
'''
      }
    }

    stage('stage 2') {
      steps {
        sh 'echo pwd'
      }
    }

  }
}