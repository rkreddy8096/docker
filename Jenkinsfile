pipeline {
    agent { labbel "jdk-11" }
    stages {
        stage (docker installation) {
            steps {
                sh 'curl -fsSL https://get.docker.com -o get-docker.sh'
                sh 'sh get-docker.sh'
                sh 'sudo chmod 666 /var/run/docker.sock'
                sh 'sudo usermod -aG docker ubuntu'     
                sh 'sudo systemctl restart docker'
                sh 'docker info'

            }
        }

        stage (docker image build) {
            steps {
                sh 'docker image build --name myimage -p 8081 .'
                sh 'docker container run --name mycontainer -d myimage'
            }
        }
    }
}