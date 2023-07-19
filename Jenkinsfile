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
                    sshagent(credentials: ['vmone-key']) {
                        script {
                        def remote = [:]
                          remote.host = '3.231.156.188'
                          remote.user = 'ec2-user'
                          remote.allowAnyHosts = true
                         // Command to install packages (replace with your package manager and package names)
                        def installCommand = 'sudo yum install -y git httpd'
                        sshCommand remote: remote, command: installCommand
                        }
                    }
                    echo 'deploying website'
                    echo 'website deployed'
            }
        }
    }
}
