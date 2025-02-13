pipeline {
    agent any

    environment {
        IMAGE_NAME = "flask-app"
        CONTAINER_NAME = "flask-container"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Harsh5442/flask-cicd-task7.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t flask-app .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    bat 'docker run -d -p 5000:5000 --name flask-container flask-app'
                }
            }
        }

        stage('Post-Build Cleanup') {
            steps {
                script {
                    bat 'docker stop flask-container || true'
                    bat 'docker rm flask-container || true'
                    bat 'docker rmi flask-app || true'
                }
            }
        }
    }
}
