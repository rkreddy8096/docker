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
                sh 'docker image build -t myimage2.0 .'
                sh 'docker image ls'
                sh 'docker container run --name mycontainer2 -d -p 8080:80 myimage2.0'
                sh 'docker container ls'
            }
        }
    }
}