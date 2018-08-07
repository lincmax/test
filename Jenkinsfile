pipeline {
  agent any
  stages {
    stage('Env. Check') {
      parallel {
        stage('Resource check') {
          steps {
            echo 'Check disk capacity is enough'
          }
        }
        stage('Env Check') {
          steps {
            sh '''df /home
'''
          }
        }
        stage('error') {
          steps {
            sh '''echo "build success!"
'''
          }
        }
      }
    }
  }
}