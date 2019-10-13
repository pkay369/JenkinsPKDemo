pipeline {
  agent none
  stages {
    stage('Stage 1') {
      agent {
        node {
          label 'EnginePSR272'
        }

      }
      steps {
        sh '/e2open/bin/setup status'
      }
    }
    stage('Manual Verification') {
      steps {
        input 'Please verify the Logs and confirm to proceed'
      }
    }
    stage('Stage Final') {
      agent {
        node {
          label 'AdminPSR262'
        }

      }
      steps {
        sh '/e2open/bin/setup status'
      }
    }
    stage('Manual Verification Admin') {
      steps {
        input 'Verify Admin Logs and Confirm to proceed.'
      }
    }
  }
}