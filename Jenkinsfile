pipeline {
    agent any // Default agent for the pipeline

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
                    test -f build/index.html
                    npm test // Replace with actual test command if different
                '''
            }
        }
    }
    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}