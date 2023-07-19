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
                        def remoteHost = 'ec2-user@3.231.156.188'

                         // Command to install packages (replace with your package manager and package names)
                        def installCommand = 'sudo yum install -y git httpd'
                        sshCommand remote: remoteHost, command: installCommand
                        }
                    }
                    echo 'deploying website'
                    echo 'website deployed'
            }
        }
    }
}
