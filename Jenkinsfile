pipeline {
    agent any

    parameters {
        file(name: 'GAME_SERVER_FILE', description: 'Upload your game server build file')
    }

    environment {
        AWS_REGION = 'ap-south-1'
    }

    stages {
        stage('Prepare') {
            steps {
                script {
                    if (params.GAME_SERVER_FILE) {
                        echo "Uploaded file name: ${params.GAME_SERVER_FILE}"
                        sh """
                            #!/bin/bash
                            echo "Copying uploaded file from Jenkins master storage..."
                            cp "\${JENKINS_HOME}/jobs/${env.JOB_NAME}/builds/${env.BUILD_NUMBER}/fileParameters/${params.GAME_SERVER_FILE}" .
                            echo "Listing file in workspace:"
                            ls -lh "${params.GAME_SERVER_FILE}"
                        """
                    } else {
                        error "No file was uploaded!"
                    }
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
