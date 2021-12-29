pipeline {
  agent any
  options {
    skipDefaultCheckout(true)
  }
  stages{
    stage('clean workspace') {
      steps {
        cleanWs()
      }
    }
    stage('checkout') {
      steps {
        checkout scm
      }
    }
    stage('setup') {
      steps {
        sh 'sudo docker build -t cluster-apache-spark:3.0.2 .'
        sh 'sudo docker-compose up -d'
      }
    }
  }
  post {
    always {
      cleanWs()
    }
  }
}
