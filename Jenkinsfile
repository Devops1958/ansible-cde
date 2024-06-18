pipeline{
    agent any
    
    stages{
        stage('zip the file'){
            steps{
                sh 'zip ansible-${BUILD_ID}.zip* --exclude Jenkinsfile'
            }
        }
        stage('upload artifacts to jfrog'){
            steps{
                sh 'curl -uadmin:APAtrqGdCmQEVEvzSAvbZF6a9tv -T \
                ansible-${BUILD_ID}.zip \
                "http://35.174.207.152:8081/artifactory/ansible/ansible-${BUILD_ID}.zip"'
            }
        }
        stage('publish to ansible server'){
            steps{
                
            }
        }
    }
}