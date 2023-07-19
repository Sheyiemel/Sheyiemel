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
                        sh 'ssh -o StrictHostKeyChecking=no ec2-user@ec2-3-231-156-188.compute-1.amazonaws.com'
                        sh 'sudo yum install -y git'
                        sh 'sudo yum install -y httpd'
                        sh 'sudo systemctl enable httpd'
                        sh 'sudo systemctl start httpd'
                        sh 'sudo rm -rf /var/www/html'
                        sh 'sudo rm -rf /var/www'
                        sh 'sudo git clone https://github.com/Sheyiemel/Sheyiemel.git /var/www/html'
                    }
                    echo 'deploying website'
                    echo 'website deployed'
                }
            }
        }
    }
}
