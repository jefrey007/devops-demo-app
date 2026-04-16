pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/jefrey007/devops-demo-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp .'
            }
        }

        stage('Tag Image') {
            steps {
                sh 'docker tag myapp jefrey2001/devops-demo-app:v1'
            }
        }

        stage('Push to DockerHub') {
            steps {
                sh 'docker push jefrey2001/devops-demo-app:v1'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop myapp || true
                docker rm myapp || true
                docker run -d -p 8083:80 --name myapp jefrey2001/devops-demo-app:v1
                '''
            }
        }
    }
}