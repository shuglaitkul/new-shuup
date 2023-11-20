pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/shuglaitkul/new-shuup.git'
            }
        }

        stage('Build') {
            steps {
                sh 'pip install -r requirements.txt'
                sh 'python manage.py compile'
            }
        }

        stage('Test') {
            steps {
                sh 'python manage.py test'
                sh 'python manage.py test --settings=integration.settings'
            }
        }

        stage('Deploy') {
            steps {
                sh 'python manage.py collectstatic --noinput'
                sh 'rsync -avz static/ <production_server>:/path/to/webroot/static/'
                sh 'rsync -avz media/ <production_server>:/path/to/webroot/media/'
                sh 'sudo service nginx restart'
            }
        }
    }
}
