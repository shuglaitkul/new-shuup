pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-jenkins-new', url: 'https://github.com/shuglaitkul/new-shuup.git']])
            }
        }
        
        stage('Build') {
            steps {
                sh 'python3 "shuup-venv\Scripts\activate"'
            }
        }

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

