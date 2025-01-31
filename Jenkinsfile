pipeline {
    agent any
    stages {
        stage('Cleanup') {
            steps {
                echo 'Cleaning up previous containers..'
                sh 'docker ps -a -q | grep . && docker rm -f $(docker ps -a -q) || true'
                sh 'pwd && ls -la'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nodejs-project .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name nodejs-app nodejs-project'
            }
        }
    }
}