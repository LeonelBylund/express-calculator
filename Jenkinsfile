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
            when {
                anyOf {
                    branch 'develop'
                    branch 'main'
        }
      }
            steps {
                bat 'npm run integration-test'
            }
        }
        stage('Delivery') {
            when {
                branch 'main'
            }
            docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                def imagre = docker.build("leonelbylunddocker/express-calculator")
                image.push()
            }
        }

        //stage('Deploy') {
            //steps {
                //echo 'Deploying...'
            //}
        //}
    }
}