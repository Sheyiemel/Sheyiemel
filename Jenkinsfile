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
                        sh 'ssh -o StrictHostKeyChecking=no ec2-user@44.192.58.26'
                    }
                    echo 'website deploying'
                        sh 'systemctl start httpd'
                        sh 'systemctl enable httpd'
                        sh 'rm -rf /var/www/html'
                        sh 'rm -rf /var/www'
                        sh 'git clone https://github.com/Sheyiemel/Sheyiemel.git /var/www/html'
                    echo 'website deployed'
                }
            }
        }

    }
}
