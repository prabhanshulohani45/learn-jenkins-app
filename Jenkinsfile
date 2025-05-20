pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                sh '''
                   ls -la
                   node --version
                   npm --version
                   npm config set cache /tmp/.npm-cache --global
                   npm ci
                   npm run build
                   ls -al
                '''
            }
        }
    }
}
