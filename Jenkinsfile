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
                        def remoteHost = '3.231.156.188'
                        def remoteUser = 'ec2-user'

                         // Command to install packages (replace with your package manager and package names)
                        def installCommand = 'sudo yum install -y git httpd'
                        sh 'sudo systemctl enable httpd'
                        sh 'sudo systemctl start httpd'
                        sh 'sudo rm -rf /var/www/html'
                        sh 'sudo rm -rf /var/www'
                        sh 'sudo git clone https://github.com/Sheyiemel/Sheyiemel.git /var/www/html'
                        sshCommand remote: remoteHost, user: remoteUser, command: installCommand
                        }
                    }
                    echo 'deploying website'
                    echo 'website deployed'
            }
        }
    }
}
