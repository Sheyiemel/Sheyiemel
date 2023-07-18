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
                    sshagent(['vmone-key']) {
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@44.215.68.39
                            sudo yum install -y git
                            sudo yum install -y httpd
                            sudo systemctl enable httpd
                            sudo systemctl start httpd
                            sudo rm -rf /var/www/html
                            sudo rm -rf /var/www
                            sudo git clone https://github.com/Sheyiemel/Sheyiemel.git /var/www/html"
                    }
                    echo 'website deployed'
                    echo 'website deployed'
                }
            }
        }
    }
}
