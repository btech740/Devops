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
                echo "deploying on IP"
                sh '''
                   while read line
                   do
                     server=$( echo "$line" |cut -d ' ' -f 1 )
                     IP=$( echo "$line" |cut -d ' ' -f 2 )
                   done < ${MY_FILE} '''
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
