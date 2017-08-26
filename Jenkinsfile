// -*- mode: groovy -*-
pipeline {
  agent any
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
        sshagent(['jenkins']) {
          sh 'ansible-playbook -i ansible/hosts ansible/deploy.yml -e env=' + env.BRANCH_NAME
        }
      }
    }
  }
  post {
//    always {
//      cleanWs()
//    }
    failure {
      echo "Failed."
    }
    success {
      echo "Success."
    }
  }
}