pipeline {
    agent any

    parameters {
        file(name: 'GAME_SERVER_BUILD', description: 'Upload your Linux game server build (.tar.gz)')
        string(name: 'BUILD_NAME', defaultValue: 'MyGameServer', description: 'Name of the build')
        string(name: 'BUILD_VERSION', defaultValue: 'v1.0', description: 'Version of the build')
        string(name: 'FLEET_NAME', defaultValue: 'MyGameFleet', description: 'Name of the fleet')
    }

    stages {
        stage('Placeholder') {
            steps {
                echo "Pipeline ready for Blue Ocean editing"
            }
        }
    }
}
