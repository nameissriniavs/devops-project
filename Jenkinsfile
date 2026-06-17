pipeline {


agent any

environment {
    IMAGE_NAME = "srinivasps/flask-app"
    IMAGE_TAG = "latest"
}

stages {

    stage('Checkout') {
        steps {
            checkout scm
        }
    }

    stage('Git Version') {
        steps {
            sh 'git --version'
        }
    }

    stage('Docker Version') {
        steps {
            sh 'docker --version'
        }
    }

    stage('Build Docker Image') {
        steps {
            sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG .'
        }
    }

    stage('Docker Hub Login') {
        steps {
            withCredentials([usernamePassword(
                credentialsId: 'dockerhub-creds',
                usernameVariable: 'DOCKER_USER',
                passwordVariable: 'DOCKER_PASS'
            )]) {
                sh '''
                echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
                '''
            }
        }
    }

    stage('Push Image to Docker Hub') {
        steps {
            sh 'docker push $IMAGE_NAME:$IMAGE_TAG'
        }
    }

}

post {
    success {
        echo 'Docker image pushed successfully!'
    }
    failure {
        echo 'Pipeline failed!'
    }
}


}

