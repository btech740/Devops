pipeline {
    agent any
    environment{
        MY_FILE = fileExists '/tmp/ENV/DEV'
    }
    
    stages {
        stage('build') {
            steps {
                sh 'pwd'
                echo "Hello world"
            }
        }
        stage('Deployment') {
            when { expression { MY_FILE == 'true' } }
            steps {
                
                sh 'curl 13.233.27.170:8080'
                
               echo "deploying"
                            
            }
            /*post {
                failure {
                    script  {
                        echo "Failure at Deployment Stage"
                    }
                }
            }*/
                
        }
                            
    }
}
