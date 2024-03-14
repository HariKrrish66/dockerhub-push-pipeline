pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/harikrishna66/my-nodejs.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh "docker build -t harikrishna66/my-nodejs:1.0 ."
            }
        }
        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', passwordVariable: 'PWD', usernameVariable: 'USR')]) {
                sh "docker login -u ${USR} -p ${PWD}"
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh "docker push harikrishna66/my-nodejs:1.0"
            }
        }
    }
}
