pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Dinesh-SM/deployment.git']])
            }
        }
        stage('docker build') {
            steps {
                sh 'docker ps'
                sh 'docker stop $(docker ps -q) && docker rm $(docker ps -aq)'
                sh 'docker ps'
                sh 'docker rmi $(docker images -q)'
                sh 'docker build -t my-app-image .'
                sh 'docker run -d -p 92:80 my-app-image'
            }
        }
    }
}
