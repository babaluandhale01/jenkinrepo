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
                bat '''
                composer install --no-interaction
                '''
            }
        }

        stage('Generate Key') {
            steps {
                bat '''
                if not exist .env copy .env.example .env
                php artisan key:generate
                '''
            }
        }

        stage('Test Laravel') {
            steps {
                bat '''
                php artisan --version
                php artisan route:list
                '''
            }
        }
    }
}
