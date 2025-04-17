pipeline {
    agent any

    environment {
        VENV = 'venv'
        APP_PATH = '/home/openeyesvo/fastapi-ci-cd'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Dilip-code/fastapi-ci-cd.git', credentialsId: 'c6f2ede9-e7ac-46f3-8253-ca98392cbef0'
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
