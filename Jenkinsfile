// -*- mode: groovy -*-
pipeline {
  agent any
  properties([pipelineTriggers([githubPush()])])  
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
          sh 'ansible-playbook -i ansible/hosts ansible/main.yml -e env=' + env.BRANCH_NAME
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