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
    stage('Smoke Test') {
      steps {
        echo 'Smoke test for he build validation'
      }
    }
    stage('Sanity Test') {
      steps {
        echo 'Basic Test Suite'
      }
    }
    stage('System Test') {
      parallel {
        stage('System Test') {
          steps {
            echo 'system test under lab environment'
          }
        }
        stage('Function Test') {
          steps {
            echo 'Fulle function test suite'
          }
        }
        stage('Stress Test') {
          steps {
            echo 'Stability Test..."'
          }
        }
      }
    }
    stage('Dry-Run (offline)') {
      parallel {
        stage('Dry-Run (offline)') {
          steps {
            echo 'Test in offline'
          }
        }
        stage('Interoperability Test') {
          steps {
            echo 'work w/ twillo, bandidth'
          }
        }
        stage('Logs observed') {
          steps {
            echo 'resource consuming observation'
          }
        }
      }
    }
  }
}