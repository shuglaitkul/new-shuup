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
                sh 'source shuup-venv\Scripts\activate && pip install django'
            }
        }

        stage('Test') {
            steps {
                sh 'source shuup-venv\Scripts\activate && python manage.py migrate'
            }
        }

        stage('Deploy') {
            steps {
                sh 'rsync -avz --exclude shuup-venv ./ shuglaitkul@localhost:/var/jenkins_home/workspace/shuup_pipeline'
                sh 'ssh shuglaitkul@localhost "sudo systemctl restart Localhost:8000"'
            }
        }
    }

    post {
        success {
            // Notify on success 
            echo 'Build and deployment successful!'
        }

        failure {
            // Notify on failure
            echo 'Build or deployment failed!'
        }
    }
}

