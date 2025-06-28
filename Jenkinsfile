pipeline {
    agent {
        docker {
            image 'python:3.10-alpine'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/karshhh/flask-hello-jenkins.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install --no-cache-dir -r requirements.txt'
            }
        }

        stage('Run App') {
            steps {
                sh 'python app.py &'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            sh 'pkill python || true'
        }
    }
}


