pipeline{
    agent any

    stages{
        stage('zip the file'){
            steps{
                sh 'zip ansible-${BUILD_ID}.zip * --exclude Jenkinsfile'
                sh 'ls -l'
                sh 'nproc'
            }
        }
        stage('upload artifacts to jfrog'){
            steps{
                sh 'curl -uadmin:APAtrqGdCmQEVEvzSAvbZF6a9tv -T \
                ansible-${BUILD_ID}.zip \
                "http://54.221.182.121:8081/artifactory/ansible/ansible-${BUILD_ID}.zip"'
            }
        }
    }
}
