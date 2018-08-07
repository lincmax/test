pipeline {
  agent any
  stages {
    stage('BVT') {
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
        stage('') {
          steps {
            sh '''echo "build success!"
'''
          }
        }
      }
    }
  }
}