// pipeline {
//     agent any
//      environment {
//         DOCKER_HUB_CREDENTIALS = credentials('dckr_pat_5taCC49-j0rPjl0TB_7MpR_k0hE')
//         DOCKER_USERNAME = 'prudhvisai489'
//         DOCKER_IMAGE_NAME = 'helodocker'
//     }
//     stages {
//         stage('Checkout') {
//             steps {
//                 checkout([$class: 'GitSCM', branches: [[name: 'refs/heads/docker_test']], userRemoteConfigs: [[url: 'https://github.com/Prudhvi489/docker.git']]])
//             }
//         }

//         stage('Build Docker Image') {
//             steps {
//                 sh 'docker build -t prudhvisai489/helodocker .'
//             }
//         }

//         stage('Push to Docker Hub') {
//             steps {
//                 sh "docker login -u $DOCKER_USERNAME -p $DOCKER_HUB_CREDENTIALS"
//                 sh "docker push $DOCKER_USERNAME/$DOCKER_IMAGE_NAME"
//             }
//         }
//     }
// }
// //////////////////////////////////////////////////////
pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    def imageName = "prudhvisai489/jenkinstest"
                     def dockerfilePath = "hellodocker/Dockerfile"
                    sh "docker build -t $imageName $dockerfilePath"
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                script {
                    def imageName = "prudhvisai489/jenkinstest"
                    docker.withRegistry('https://registry.hub.docker.com', 'dckr_pat_GIdPbMxSJerY1RDpMAyLYOokIJM') {
                        docker.image(imageName).push()
                    }
                }
            }
        }
    }
}
// R35N3W6UGJL7PXLRG6HEWS2QIHDIMKMR
// 2ULBQWLYYQPjww37eXQSbHL8X2A_2bKAkRTWuiTELCwzHqsBs-ngrok
// Authtoken saved to configuration file: /home/prudhvi/.config/ngrok/ngrok.yml
// docker->dckr_pat_GIdPbMxSJerY1RDpMAyLYOokIJM