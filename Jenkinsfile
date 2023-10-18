pipeline {
    agent any
    tools{
        maven 'Maven-3.9.5'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/VishaliKC/cicd-jenkins.git']]])
                bat 'mvn clean package'
                echo 'Build completed'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                bat 'mvn test'
                echo 'Testing completed'
            }
        }
        stage('Build Docker Image') {
            steps {
                echo 'Building Docker Image...'
                bat 'docker build -t vishali/cicd-jenkins:latest .'
                echo 'Docker Image Build completed'
            }
        }

    }
}