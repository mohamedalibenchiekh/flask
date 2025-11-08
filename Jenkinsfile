pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/pallets/flask.git'
            }
        }
        stage('Setup Virtual Environment') {
            steps {
                sh 'python3 -m venv venv'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh '. venv/bin/activate && pip install -e ".[async]" && pip install pytest'
            }
        }
        stage('Run Tests') {
            steps {
                sh '. venv/bin/activate && pytest'
            }
        }
    }

    post {
        always {
            // Optionally, clean up the virtual environment
            sh 'rm -rf venv'
        }
    }
}
