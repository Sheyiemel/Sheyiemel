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
                        sh 'ssh -o StrictHostKeyChecking=no ec2-user@3.228.17.244'
                    }
                }
            }
            steps {
                script {
                    echo 'website deploying'
    
                    sudo yum install -y git
                    sudo yum install -y httpd
                    sudo systemctl start httpd
                    sudo systemctl enable httpd
                    sudo rm -rf /var/www/html
                    sudo rm -rf /var/www
                    sudo git clone https://github.com/Sheyiemel/Sheyiemel.git /var/www/html
    
                    echo 'website deployed'
                }
            }
        }

    }
}
