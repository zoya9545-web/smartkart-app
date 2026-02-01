
pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps { checkout scm }
    }
    stage('Build Docker Image') {
      steps {
        sh 'docker build -t smartkart-app:latest .'
      }
    }
    stage('Deploy') {
      steps {
        sh '''
          docker stop smartkart || true
          docker rm smartkart || true
          docker run -d -p 80:80 --name smartkart smartkart-app:latest
        '''
      }
    }
  }
}
