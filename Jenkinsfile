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
        stage('Build Prox2') {
          steps {
            sh '''cd ~/linc/prox2
git fetch -a
git checkout hackathon_dragon_over_blue_ocean
git pull origin hackathon_dragon_over_blue_ocean
echo "Build prox2 done!"'''
          }
        }
        stage('Build Ecare-UI') {
          steps {
            sh '''cd ~/linc/ecare-ui
git fetch -a
git checkout hackathon_dragon_over_blue_ocean
git pull origin hackathon_dragon_over_blue_ocean
echo "Build ecare-ui done!"'''
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
        stage('Interoperability Test') {
          steps {
            echo 'work w/ twillo, bandidth'
          }
        }
        stage('Logs observation') {
          steps {
            echo 'resource consuming observation'
          }
        }
      }
    }
    stage('Go live (online)') {
      parallel {
        stage('Go live (online)') {
          steps {
            echo 'Announcement'
          }
        }
        stage('mail result') {
          steps {
            echo 'test ok'
          }
        }
      }
    }
    stage('go/no-go') {
      steps {
        input 'Go? No Go?'
      }
    }
  }
}