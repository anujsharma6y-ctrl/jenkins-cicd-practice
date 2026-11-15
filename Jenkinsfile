pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'python3 --version'
                sh 'python3 app.py'
            }
        }

        
       stage('Docker Build4') {
             steps {
                sh 'docker build -t jenkins-practice-app:latest .'
           }
       }
      stage('Docker Run') {
           steps {
               sh 'docker run --rm jenkins-practice-app:latest'
         } 
      }
      stage('Package') {
            steps {
               sh 'mkdir -p build'
               sh 'cp app.py build/'
               sh 'zip -r application.zip build/'
           }
       }
       stage('Archive') {
            steps {
             archiveArtifacts artifacts: 'application.zip',
                     fingerprint: true
           }
       }
    

stage('Parallel Checks') {
    parallel {
        stage('Python Check') {
            steps {
                sh 'python3 --version'
            }
        }

        stage('Docker Check') {
            steps {
                sh 'docker --version'
            }
        }

        stage('System Check') {
            steps {
                sh 'uname -a'
            }
        }
    }
}
