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
                sh 'curl -u<USERNAME>:<PASSWORD> -T \
                ansible-${BUILD_ID}.zip \
                "http://http://52.72.19.248:8081/artifactory/ansible/ansible-${BUILD_ID}.zip"'
            }
        }
    }
}
