pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ukamkhede-hub/sai-amrut-dairy.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t sai-amrut-dairy .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker stop sai-amrut-dairy || exit /b 0'
                bat 'docker rm sai-amrut-dairy || exit /b 0'
                bat 'docker run -d -p 8083:80 --name sai-amrut-dairy sai-amrut-dairy'
            }
        }
    }
}