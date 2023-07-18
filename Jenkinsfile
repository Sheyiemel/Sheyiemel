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
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@44.215.68.39 \n
                            sudo yum install -y git \n
                            sudo yum install -y httpd \n
                            sudo systemctl enable httpd \n
                            sudo systemctl start httpd \n
                            sudo rm -rf /var/www/html \n
                            sudo rm -rf /var/www \n
                            sudo git clone https://github.com/Sheyiemel/Sheyiemel.git /var/www/html"
                    }
                    echo 'website deployed'
                    echo 'website deployed'
                }
            }
        }
    }
}
