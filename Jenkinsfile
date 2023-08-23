pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('dckr_pat_GIdPbMxSJerY1RDpMAyLYOokIJM')
        IMAGE_NAME = 'prudhvisai489/jenkinstest'
        DOCKERFILE_PATH = 'hellodocker/Dockerfile' // Adjust the path to your Dockerfile
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    def dockerImage = docker.build("${IMAGE_NAME}", "-f ${DOCKERFILE_PATH} .")

                    // Tag the image with the final name
                    dockerImage.tag("${IMAGE_NAME}:latest")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', DOCKER_HUB_CREDENTIALS) {
                        dockerImage.push()
                    }
                }
            }
        }
    }

    post {
        success {
            echo "Image successfully built and pushed to Docker Hub"
        }
        failure {
            echo "Image build or push failed"
        }
    }
}
