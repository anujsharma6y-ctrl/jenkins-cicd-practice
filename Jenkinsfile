pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Code fetched from GitHub'
            }
        }

        stage('Build') {
            steps {
                sh 'python3 app.py'
            }
        }
    }
}
