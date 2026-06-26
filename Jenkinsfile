pipeline {
    agent any

    environment {
       	DOCKERHUB_CREDENTIAL = credentials('dockerhub-creds')
        IMAGE_NAME = 'vyankatesh23/jenkins-cicd-app'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
         
        stage('Build Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:latest .'
            }
        }
        
        stage('login to docker hub') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIAL_PSW | docker login -u $DOCKERHUB_CREDENTIAL_USR --password-stdin'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $IMAGE_NAME:latest'
            }
        }
    }
}
