pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/aankitOfficial1/Banking-java-project.git'
                echo 'GitHub repository checked out'
            }
        }
        stage('Compile Code') {
            steps {
                echo 'Starting compilation'
                sh 'mvn compile'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Code Quality Check') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('Package Application') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myimg .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh 'docker run -dit --rm -p 8091:8091 --name c000 myimg'
            }
        }
    }
}
