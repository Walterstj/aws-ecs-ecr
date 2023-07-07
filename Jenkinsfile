pipeline {
    agent any
    environment{
      ECR_CREDENTIALS = credentials('docker-creds')
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t bftapah1/webapp:1.0.2 .'
            }
        }
        stage('Login') {
            steps {
                sh 'echo $ECR_CREDENTIALS_PSW | docker login -u $ECR_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push') {
            steps {
                sh 'docker push bftapah1/webapp:1.0.2'
            }
        }
        stage('Logout') {
            steps {
                sh 'docker logout'
            }
        }
    }
}
