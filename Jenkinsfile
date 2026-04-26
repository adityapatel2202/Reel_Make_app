pipeline {
    agent any

    environment {
        PYTHON_EXE = 'D:\CodeWithHarry python\VidSnapAI\Reel_Make_app\venv\Scripts\python.exe'
    }

    stages {
        stage('Install Dependencies') {
            steps {
                bat '"%PYTHON_EXE%" -m pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat '"%PYTHON_EXE%" -m pytest'
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