pipeline {
    agent any
    environment {
            CI = 'true'
        }
    stages {
        stage('Install') {
            steps {
                sh 'yarn install'
            }
        }

        stage('Test') {
            steps {
                sh 'yarn test'
            }
        }

        stage('SonarQube Analysis') {

            tools {
                sonarQube 'SonarQubeScanner'
            }

            steps{

                withSonarQubeEnv('SonarQubeServer'){
                    sh 'sonar-scanner'
                }

            }
        }

        stage('Build') {
            steps {
                sh 'yarn build'
            }
        }
        
        stage('Git Checkout') {
            steps {
                sh 'git status'
                sh 'git add .'
            }
        }
    }
}