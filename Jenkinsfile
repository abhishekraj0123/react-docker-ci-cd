pipeline {
    agent any

    tools {
        nodejs "NodeJS 18"  // You must install NodeJS in Jenkins tools
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/abhishekraj0123/react-docker-ci-cd.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('SonarQube Code Analysis') {
            environment {
                SONAR_TOKEN = credentials('sonar-token') // Add your SonarQube token in Jenkins Credentials
            }
            steps {
                withSonarQubeEnv('MySonarServer') {
                    sh 'npx sonar-scanner'
                }
            }
        }
    }
}
