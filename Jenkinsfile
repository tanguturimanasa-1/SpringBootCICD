pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t springboot-cicd:latest .'
            }
        }

        stage('Docker Run') {
            steps {
                bat '''
                docker stop springboot-cicd-container || exit 0
                docker rm springboot-cicd-container || exit 0
                docker run -d -p 8080:8080 --name springboot-cicd-container springboot-cicd:latest
                '''
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }
        failure {
            echo 'CI/CD Pipeline failed!'
        }
    }
}
