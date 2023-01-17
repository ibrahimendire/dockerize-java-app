pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/ibrahimendire/dockerize-java-app.git'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t ibrahimendire/image:latest .'
            }
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    sh "docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD"
                    sh 'docker push ibrahimendire/image:latest'
                }
            }
        }
    }
}
