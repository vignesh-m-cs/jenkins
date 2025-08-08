pipeline {
  agent any
  stages {
    stage('Set AWS Credentials & List EC2') {
      steps {
        script {
          withAWS(credentials: 'aws2', region: "${AWS_REGION}") {
            sh """
            #!/bin/bash
            echo "Listing EC2 instances in ${AWS_REGION}..."
            aws ec2 describe-instances --output table
            """
          }
        }

      }
    }

  }
  environment {
    AWS_REGION = 'ap-south-1'
  }
  parameters {
    file(name: 'GAME_SERVER_FILE', description: 'Upload your game server build file')
  }
}