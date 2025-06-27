pipeline {
    agent {
        docker {
            image 'python:3.10-alpine'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/karshhh/flask-hello-jenkins.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run App') {
            steps {
                sh 'nohup python app.py & sleep 5'
                sh 'curl http://localhost:5000'
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
