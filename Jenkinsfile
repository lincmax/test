pipeline {
  agent any
  stages {
    stage('Env. Check') {
      parallel {
        stage('Welcome') {
          steps {
            echo 'Welcome!'
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