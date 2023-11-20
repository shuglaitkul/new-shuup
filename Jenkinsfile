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
                sh 'python -m venv shuup-venv'
                sh 'shuup-venv\Scripts\activate && pip install django'
            }
        }

        stage('Test') {
            steps {
                sh 'source shuup-venv\Scripts\activate && python manage.py migrate'
            }
        }

        // stage('Deploy') {
        //     steps {
                
        //     }
        // }
    }
}

