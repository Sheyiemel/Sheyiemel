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
                script {
                        def remoteHost = '3.231.156.188'
                        def remoteUser = 'ec2-user'

                         // Command to install packages (replace with your package manager and package names)
                        def installCommand = 'sudo yum install -y git httpd'
                        sshCommand remote: remoteHost, user: remoteUser, command: installCommand
                }
                    echo 'deploying website'
                    echo 'website deployed'
            }
        }
    }
}
