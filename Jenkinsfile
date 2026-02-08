pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code checked out from GitHub'
            }
        }

        stage('Build') {
            steps {
                sh 'ls'
            }
        }

        stage('Test') {
            steps {
                sh 'cat app.txt'
            }
        }

        stage('Docker Build') {
            steps {
                sh '/usr/local/bin/docker build -t jenkins-demo:1.0 .'
            }
        }

        stage('Docker Run') {
            steps {
                sh '''
                    /usr/local/bin/docker rm -f demo-container || true
                    /usr/local/bin/docker run --name demo-container jenkins-demo:1.0
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully 🎉'
        }
        failure {
            echo 'Pipeline failed ❌'
        }
    }
}

