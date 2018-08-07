pipeline {
  agent any
  stages {
    stage('Resource check') {
      steps {
        echo 'Check disk capacity is enough'
      }
    }
    stage('Build Making') {
      parallel {
        stage('Build Making') {
          steps {
            echo 'D/L or git clone source code'
          }
        }
        stage('D/L or git clone src code') {
          steps {
            sh 'echo "git clone ..."'
          }
        }
        stage('Start building') {
          steps {
            echo 'start build process...'
          }
        }
      }
    }
  }
}