pipeline {
  agent none
  stages {
    stage('Stage 1') {
      parallel {
        stage('Stage 1') {
          agent {
            node {
              label 'EInvoice'
            }

          }
          steps {
            sh '/e2open/bin/setup list'
          }
        }
        stage('Stage 2') {
          agent {
            node {
              label 'devbox'
            }

          }
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