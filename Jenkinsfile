pipeline {
    agent any // Default agent for the pipeline

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine' // Fixed typo: 'iamge' -> 'image'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -al
                    echo 'Hello World'
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine' // Fixed syntax for docker agent
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo 'Running tests...'
                    npm test // Example test command; replace with actual test command
                '''
            }
        }
    }
}