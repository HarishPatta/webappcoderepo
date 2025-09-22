pipeline {
    agent any
    tools {
        maven 'Maven 3.8.6'
    }
    stages {
        stage('Code Checkout') {
            steps {
                git credentialsId: '<Git Credentials>', url: '<GitHub URL>'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t <dockerhub>/<image>:${BUILD_NUMBER} .'
            }
        }
        stage('Push Image') {
            steps {
                sh 'docker login -u <Username> -p <Password>'
                sh 'docker push <dockerhub>/<image>:${BUILD_NUMBER}'
            }
        }
    }
}
