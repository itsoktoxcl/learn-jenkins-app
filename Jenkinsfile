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

        stage('Test'){
            agent {
                docker 'node:18-alpine'
                reuseNode true
            }
        } 
           steps {
                sh '''
                test -f build/index.html
                  npm test
                '''
        }
    }
}
