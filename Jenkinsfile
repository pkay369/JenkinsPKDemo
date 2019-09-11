pipeline {
  agent none
  stages {
    stage('Stage 1') {
      parallel {
        stage('Stage 1') {
          steps {
            node(label: 'EInvoice') {
              echo 'This stage is handled on EInvoice box'
            }

            sh '/e2open/bin/setup list'
          }
        }
        stage('Stage 2') {
          steps {
            node(label: 'devbox') {
              echo 'handled on e2dev0107'
            }

            sh '/e2open/bin/setup list'
          }
        }
        stage('Stage 3') {
          steps {
            echo 'Dummy Stage'
          }
        }
      }
    }
    stage('Manual Verification') {
      steps {
        input 'Please verify the Logs and confirm to proceed'
      }
    }
    stage('Stage Final') {
      steps {
        echo 'Going to Deploy on all boxes in parallel'
      }
    }
  }
}