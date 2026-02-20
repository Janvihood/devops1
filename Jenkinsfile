pipeline {
  agent any

  stages {

    stage('Clone') {
      steps {
        checkout scm
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t devops-app .'
      }
    }

    stage('Run Container') {
      steps {
        sh 'docker stop app || true'
        sh 'docker rm app || true'
        sh 'docker run -d -p 5000:5000 --name app devops-app'
      }
    }
  }
}
