pipeline {
    agent any

    stages {
        stage('no docker') {
            steps {
                sh ''' 
                    echo "No Docker"
                    ls -la
                    touch container_no.txt
                '''
            }
        }
     stage('with docker') {
         agent{
             docker {
                 image 'node:18-alpine'
                 reuseNode true
             }
             
         }
            steps {
                sh ''' 
                    echo "with Docker"
                    ls -la
                    touch conatiner_yes.txt
                
                '''
                
            }
        }    
    }
}
