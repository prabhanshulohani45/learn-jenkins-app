pipeline {
    agent any

    stages {
        stage('Clean Checkout') {
            steps {
                cleanWs()
                checkout scm
            }
        }
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                    args '-u 981:981' // ensures same UID:GID as Jenkins workspace
                }
            }

            steps {
                sh '''
                   ls -la
                   node --version
                   npm --version

                   mkdir -p ./npm-cache
                   npm ci --cache ./npm-cache
                   npm run build

                   ls -al
                '''
            }
        }
    }
}