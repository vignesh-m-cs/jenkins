pipeline {
    agent any

    parameters {
        file(name: 'GAME_SERVER_FILE', description: 'Upload your game server build file')
    }

    environment {
        AWS_REGION = 'ap-south-1' // Change to your AWS region
    }

    stages {
        stage('Prepare') {
            steps {
                echo "Uploaded file: ${params.GAME_SERVER_FILE}"
                sh 'ls -lh "${params.GAME_SERVER_FILE}"'
            }
        }

        stage('Set AWS Credentials & List EC2') {
            steps {
                withAWS(credentials: 'aws2', region: "${AWS_REGION}") {
                    sh 'aws ec2 describe-instances --output table'
                }
            }
        }
    }
}
