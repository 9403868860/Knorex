pipeline {
    agent any

    stages {
        stage('Build Image') {
            steps {
                script {
                    docker.build("my-flask-app:${env.BUILD_NUMBER}")
                }
            }
        }

        stage('Test Image') {
            steps {
                // Add test commands here if needed
            }
        }

        stage('Deploy Image') {
            steps {
                script {
                    // Docker Hub credentials should be configured in Jenkins
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        docker.image("my-flask-app:${env.BUILD_NUMBER}").push()
                    }
                }
            }
        }
    }
}
