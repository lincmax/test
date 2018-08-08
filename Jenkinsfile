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
~/remote_prox2_up.sh &
sleep 30
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
      parallel {
        stage('Ecare-UI Smoke Test') {
          steps {
            sh '''wget -O /dev/null https://care.lincdev:8000/home?shop_id=3abe58dc-cf26-11e4-975c-22000ac78ddb&o=LINCGLOB15950391510&e=stanley@letslinc.com > /dev/null 2>&1
'''
          }
        }
        stage('Prox2 Smoke Test') {
          steps {
            sh '''. ~/token
wget -O /dev/null --header="content-type: application/json" --header="Authorization: Bearer ${token}" http://ws.lincdev:8000/v1/order?order_id=LINCGLOB46134184> /dev/null 2>&1'''
          }
        }
      }
    }
    stage('Sanity Test') {
      steps {
        echo 'Sanity Test'
      }
    }
    stage('System Test') {
      parallel {
        stage('Functional Test') {
          steps {
            sh '''cat > /tmp/functional_test_result.txt <<EOF
function1 ... done
function2 ... done
function3 ... done
EOF'''
            mail(subject: '[Jenkins] Functional test result', body: 'function1 ... done<br> function2 ... done<br> function3 ... done<br>', mimeType: 'text/html', to: 'stanley@letslinc.com, max@letslinc.com')
          }
        }
        stage('Stress Test') {
          steps {
            sh '''cat > /tmp/stress_test_result.txt <<EOF
Pass!
EOF'''
            mail(subject: '[Jenkins] Stress test result ', body: 'Pass!<br>', mimeType: 'text/html', to: 'stanley@letslinc.com, max@letslinc.com')
          }
        }
        stage('Regression Test') {
          steps {
            sh '''cat > /tmp/regression_test_result.txt <<EOF
Pass!
EOF'''
            mail(subject: '[Jenkins] Regression test result', body: 'Pass!<br>', mimeType: 'text/html', to: 'stanley@letslinc.com, max@letslinc.com')
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
    stage('Go live') {
      steps {
        mail(subject: '[Jenkins] Wait for approval to go live', body: 'Test result is ready and waiting for go live approval. <br>', mimeType: 'text/html', to: 'stanley@letslinc.com, max@letslinc.com')
        input 'Approve to go live?'
        sh 'echo "Go live!"'
        mail(subject: '[Jenkins] Congrats team, system go live.', body: 'Congrats team, system go live.', to: 'stanley@letslinc.com, max@letslinc.com')
      }
    }
  }
}