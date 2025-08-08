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
                script {
                    echo "Uploaded file: ${params.GAME_SERVER_FILE}"
                    sh """
                        #!/bin/bash
                        echo "Listing uploaded file:"
                        ls -lh "${params.GAME_SERVER_FILE}"
                    """
                }
            }
        }

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
}
