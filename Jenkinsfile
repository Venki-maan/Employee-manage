pipeline {

    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'master',
                url: 'https://github.com/Venki-maan/Employee-manage.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Check Versions') {
            steps {
                sh 'node --version'
                sh 'npm --version'
            }
        }

        stage('Check Date') {
            steps {
                sh 'date'
            }
        }
      
        stage('Docker Build') {
            steps {
                sh 'docker build -t employee-app .'
            }
        }

    }

    post {

        always {
            echo 'Pipeline completed'
        }

        success {
            echo 'Application build successful'
        }

        failure {
            echo 'Application build failed'
        }

    }

}
