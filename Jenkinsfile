pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'studenthub',
                    url: 'https://github.com/annapoorna-k/studenthub.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker compose up -d --build'
            }
        }

        stage('Image') {
            steps {
                sh 'docker images'
            }
        }

        stage('Tag Image') {
            steps {
                sh 'docker tag studenthub2-app:latest yashuraj/studenthub2-app:latest'
            }
        }

        stage('Push') {
            steps {
                sh 'docker push yashuraj/studenthub2-app:latest'
            }
        }

        stage('Deploy') {
            steps {
                sh 'kubectl apply -f deployment.yml'
            }
        }
    }
}
