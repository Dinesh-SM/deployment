pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/deploymwntgreen']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Dinesh-SM/deployment.git']])
            }
        }
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
