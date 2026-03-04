pipeline {
    agent any

    environment {
        IMAGE_NAME = "danish-node-app"
        CONTAINER_NAME = "danish-running-app"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f $CONTAINER_NAME || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 3000:3000 --name $CONTAINER_NAME $IMAGE_NAME'
            }
        }

        stage('List Running Containers') {
            steps {
                sh 'docker ps'
            }
        }
    }
}
