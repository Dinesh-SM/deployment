pipeline {
    agent {
        lable 'work'
    }
    stages {
        stage('docker build') {
            steps {
                sh 'docker ps'
                sh 'docker stop $(docker ps -q) && docker rm $(docker ps -aq)'
                sh 'docker ps'
                sh 'docker rmi $(docker images -q)'
                sh 'docker build -t green-app-image .'
                sh 'docker run -d -p 93:80 green-app-image'
            }
        }
    }
}
