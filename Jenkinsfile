pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sudo yum install -y git
                sudo yum install -y httpd
                sudo systemctl start httpd
                sudo systemctl enable httpd
                sudo rm -rf /var/www/html
                sudo rm -rf /var/www
                sudo git clone https://github.com/Sheyiemel/Sheyiemel.git /var/www/html 
            }
        }
        stage('Deploy') {
            steps {
              echo 'website deployed'
            }
        }
    }
}
