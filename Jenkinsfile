pipeline {
    agent { label "jdk-11" }
    stages {
        stage (dockerinstallation) {
            steps {
                sh 'curl -fsSL https://get.docker.com -o get-docker.sh'
                sh 'sh get-docker.sh'
                sh 'sudo chmod 666 /var/run/docker.sock'
                sh 'sudo usermod -aG docker ubuntu'     
                sh 'sudo systemctl restart docker'
                sh 'docker info'

            }
        }

        stage (dockerimagebuild) {
            steps {
                sh 'docker image build -t myimage .'
                sh 'docker image ls'
                sh 'docker container run -d --name mycontainer -p 8081:8080  myimage'
                sh 'docker container ls'
            }
        }
    }
}