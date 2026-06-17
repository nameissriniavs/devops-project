pipeline {

    agent any

    stages {

        stage('Git Check') {
            steps {
                sh 'git --version'
            }
        }

        stage('Docker Check') {
            steps {
                sh 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app:test .'
            }
        }

    }
}
