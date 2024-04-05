pipeline {
    agent any
    stages {
        stage('docker build') {
            steps {
                sh 'docker ps'
                sh 'docker ps -q | xargs docker stop || true'
                sh 'docker ps -aq | xargs docker rm || true'
                sh 'docker ps'
                sh 'docker rmi $(docker images -q)'
                sh 'docker build -t green-app-image .'
                sh 'docker run -d -p 93:80 green-app-image'
            }
        }
    }
}
