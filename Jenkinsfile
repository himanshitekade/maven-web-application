pipeline {
    agent any
    stages {
        stage('Source Code Management') {
            steps {
                git 'https://github.com/himanshitekade/maven-web-application.git'
            }
        }
        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ht-maven-web-app .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh '''
                    docker rm -f ht-maven-web-container || true
                    docker run -d --name ht-maven-web-container -p 8081:8080 ht-maven-web-app
                '''
            }
        }
    }
}
