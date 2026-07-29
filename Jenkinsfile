pipeline {

    agent any

    stages {

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
                sh 'docker build -t employee-app:${BUILD_NUMBER} .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker stop employee-app || true'
                sh 'docker rm employee-app || true'
                sh 'docker run -d --name employee-app -p 3000:3000 employee-app'
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

