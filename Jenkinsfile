pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'npm install'
            }
        }
        stage('Unit Test') {
            steps {
                bat 'npm run unit-test'
            }
        }
        stage('Integration Test') {
            steps {
                bat 'npm run integration-test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}