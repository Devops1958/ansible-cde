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
                "http://54.83.130.198:8081/artifactory/ansible/ansible-&{BUILD_ID}.zip"'
            }
        }
        stage('publish to ansible server '){
            steps{
                sshPublisher(publishers: [sshPublisherDesc(configName: 'Ansible-server', \
                transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: \
                'ls ', execTimeout: 120000, flatten: false, makeEmptyDirs: false, \
                noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: \
                '.', remoteDirectorySDF: false, removePrefix: '', \
                sourceFiles: 'ansible*zip')], usePromotionTimestamp: false, \
                useWorkspaceInPromotion: false, verbose: false)])
            }
        }
    }
}
        
            
    