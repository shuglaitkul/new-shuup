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
                script {
                    sh 'docker build -t shuup-shuup .'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh 'docker run shuup-shuup pytest'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'docker push shuup-shuup'
                }
            }
        }
    }
}
