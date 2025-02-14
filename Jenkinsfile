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
                npm ci
                npm run build
                ls -la
                npm audit fix
                '''
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Test Stage"'
                sh 'test build/index.html'
                sh 'npm test'
            }
        }
    }
}
