pipeline {
    agent any

    tools { go 'go1.17' }

    environment {
        API_PORT = '8888'
        DB_HOST = '10.10.100.12'
    }

    stages {
        stage('build') {
            steps {
                sh 'go version'
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps"
                    ls -lah
                '''
            }
        }
        stage('delivery') {
            steps {
                echo "API_PORT is ${API_PORT}"
                echo "DB_HOST is ${DB_HOST}"
            }
        }
        stage('Deploy - Staging') {
            steps {
                echo "Deploy to staging"
            }
        }

        stage('Sanity check') {
            steps {
                input "Does the staging environment look ok?"
            }
        }

        stage('Deploy - Production') {
            steps {
                echo "Deploy to production"
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
    }
}