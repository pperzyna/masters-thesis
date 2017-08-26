// -*- mode: groovy -*-
properties([pipelineTriggers([githubPush()])])
pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr:'3'))
    ansiColor('gnome-terminal')
  }
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
          sh 'ansible-playbook -i ansible/hosts ansible/main.yml -e \'host_key_checking=False\'  -e env=' + env.BRANCH_NAME
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