// -*- mode: groovy -*-
pipeline {
  stages {
    stage ('Download') {
      steps {
        checkout scm
      }
    }
    stage ('Install') {
      steps {
         echo "Install"
      }
    }
    stage ('Test') {
      steps {
         echo "Test"
      }
    }
    stage ('Deploy') {
      steps {
         echo "Deploy."
      }
    }
  }
  post {
    always {
//      cleanWs()
    }
    failure {
      echo "Failed."
    }
    success {
      echo "Success."
    }
  }
}