pipeline {

    agent any

    stages {

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
                sh 'docker build -t srinivasps/flask-app:latest .'
            }
        }

        stage('List Images') {
            steps {
                sh 'docker images'
            }
        }

    }
}
