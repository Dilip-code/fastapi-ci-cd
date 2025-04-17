pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps {
                git credentialsId: 'github-pat', url: 'https://github.com/Dilip-code/fastapi-ci-cd.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }
        stage('Run App') {
            steps {
                sh 'nohup ./venv/bin/uvicorn app.main:app --host 0.0.0.0 --port 8000 &'
            }
        }
    }
}
