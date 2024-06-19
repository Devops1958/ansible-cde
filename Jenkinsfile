pipeline{
    agent any
     
    stages{
        stage(' zip the file'){
            steps{
                sh 'zip ansible-${BUILD_ID}.zip * --exclude Jenkinsfile'
                sh 'cat /etc/os-release' 
            }
        }
        stage('upload the artifact'){
            steps{
                sh 'curl -uadmin:APAtrqGdCmQEVEvzSAvbZF6a9tv -T \
                ansible-${BUILD_ID}.zip \
                "http://35.168.2.178:8081/artifactory/ansible/ansible-${BUILD_ID}.zip"'
            }
        }
        stage('publish to ansible server'){
            steps{
                 sshPublisher(publishers: [sshPublisherDesc(configName: 'Ansible-server', \
                 transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: \
                 'ls ', execTimeout: 120000, flatten: false, makeEmptyDirs: false, \
                 noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: \
                 '/home/ec2-user', remoteDirectorySDF: false, removePrefix: '', \
                 sourceFiles: 'ansible-${BUILD_ID}.zip')], usePromotionTimestamp: false, \
                 useWorkspaceInPromotion: false, verbose: false)])
            }
        }
    }
    
}