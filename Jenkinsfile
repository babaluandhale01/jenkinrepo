pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/babaluandhale01/jenkinrepo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                composer install --no-interaction
                '''
            }
        }

        stage('Generate Key') {
            steps {
                sh '''
                cp .env.example .env
                php artisan key:generate
                '''
            }
        }

        stage('Test Route') {
            steps {
                sh '''
                php artisan route:list
                '''
            }
        }
    }
}
