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
                        sh 'ssh -o StrictHostKeyChecking=no root@44.192.58.26'
                    }
                    echo 'website deploying'
                        sh 'git clone https://github.com/Sheyiemel/Sheyiemel.git /var/www/html'
                    echo 'website deployed'
                }
            }
        }

    }
}
