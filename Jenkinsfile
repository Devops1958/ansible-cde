pipeline{
    agent any
     
    stages{
        stage(' zip the file'){
            steps{
                sh 'zip ansible-${BUILD_ID}.zip * --exclude Jenkinsfile'
                sh 'cat /etc/os-release' 
            }
        }
    }
    
}