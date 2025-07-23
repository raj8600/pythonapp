pipeline {
    agent any

    environment {
        IMAGE_NAME = 'my-python-app'
        DOCKER_REGISTRY = 'prayagrajingle8600'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/raj8600/pythonapp.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKER_REGISTRY}/${IMAGE_NAME}")
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                withDockerRegistry([credentialsId: 'dockerhub-creds', url: '']) {
                    script {
                        docker.image("${DOCKER_REGISTRY}/${IMAGE_NAME}").push('latest')
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage - implement your deployment logic here'
                // e.g., docker run, kubectl apply, etc.
            }
        }
    }
}
