pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/adityapatel2202/Reel_Make_app.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'python -m pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t reel-make-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker run -d -p 5000:5000 --name reel-make-app reel-make-app'
            }
        }
    }
}