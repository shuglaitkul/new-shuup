pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-jenkins-new', url: 'https://github.com/shuglaitkul/new-shuup.git']])
            }
        }
        
        // stage('Build') {
        //     steps {
        //         sh 'python -m venv shuup-venv'
        //         sh 'shuup-venv\\Scripts\\activate && pip install django'
        //     }
        // }

        // stage('Test') {
        //     steps {
        //         sh 'shuup-venv\\Scripts\\activate && python manage.py migrate'
        //     }
        // }

        // stage('Deploy') {
        //     steps {
                
        //     }
        // }
    }
}

