pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo "Build Docker Image"
                bat "docker build -t aruna/kuborep:latest ."
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub',
                    usernameVariable: 'DOCKER_USERNAME',
                    passwordVariable: 'DOCKER_PASSWORD'
                )]) {

                    bat "docker login -u %DOCKER_USERNAME% -p %DOCKER_PASSWORD%"
                    bat "docker push aruna/kuborep:latest"
                }
            }
        }
    }
}