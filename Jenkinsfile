pipeline {
    agent {
        label 'docker-agent-python'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install --no-cache-dir -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest -v'
            }
        }

        stage('Run Script') {
            steps {
                sh 'python calculator.py'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed - check the stage logs above.'
        }
    }
}
