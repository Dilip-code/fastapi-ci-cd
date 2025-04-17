pipeline {
    agent any

    environment {
        VENV = 'venv'
        APP_PATH = '/home/openeyesvo/fastapi-ci-cd'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'git@github.com:YOUR_USERNAME/fastapi-ci-cd.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                dir("${APP_PATH}") {
                    sh '''
                        python3 -m venv ${VENV}
                        . ${VENV}/bin/activate
                        pip install --upgrade pip
                        pip install -r requirements.txt
                    '''
                }
            }
        }

        stage('Restart FastAPI App') {
            steps {
                sh 'sudo systemctl restart fastapi-app'
            }
        }
    }
}
