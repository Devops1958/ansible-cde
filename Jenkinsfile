pipeline{
    agent any

    stages{
        stage(' zip the file'){
            steps{
                sh 'rm -rf *.zip || echo ""'
                sh 'zip -r ansible-${BUILD_ID}.zip  *  --exclude Jenkinsfile'
                sh 'cat /etc/os-release'
            }
        }
        stage('upload to artifact'){
            steps{
                sh 'curl -uadmin:APAtrqGdCmQEVEvzSAvbZF6a9tv -T \
                ansible-${BUILD_ID}.zip \
                "http://35.168.2.178:8081/artifactory/ansible/ansible-&{BUILD_ID}.zip"'
            }
        }
    }
}
        
            
    