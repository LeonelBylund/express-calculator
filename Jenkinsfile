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
        stage('Deliver-image') {
            when {
                branch 'main'
            }
            steps {
                script{
            docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                def imagre = docker.build("leonelbylunddocker/express-calculator")
                image.push("$BUILD_ID")
                    }
                }
            }
        }

        //stage('Deploy') {
            //steps {
                //echo 'Deploying...'
            //}
        //}
    }
}