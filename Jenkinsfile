pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'building website'
            }
        }
        stage('Deploy') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'vmone-key', keyFileVariable: 'identity', passphraseVariable: '', usernameVariable: 'ec2-user')]) {
        remote.user = userName
        remote.identityFile = identity
                def remote = [:]
                    remote.name = 'vmone'
                    remote.host = '3.231.156.188'
                    remote.user = 'ec2-user'
                    remote.allowAnyHosts = true
                    remote.identityFile = 'identity'
                         // Command to install packages (replace with your package manager and package names)
                def installCommand = 'sudo yum install -y git httpd'
                sshCommand remote: remote, command: installCommand
                
                echo 'deploying website'
                echo 'website deployed'
            }
        }
    }
}
