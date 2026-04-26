pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                bat 'py -m pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'py -m pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t reel-make-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat '''
                docker stop reel-make-app || exit 0
                docker rm reel-make-app || exit 0
                docker run -d -p 5000:5000 --name reel-make-app reel-make-app
                '''
            }
        }
    }
}