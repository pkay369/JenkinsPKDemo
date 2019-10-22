pipeline {
  agent none
  stages {
    stage('Engine Restart') {
      agent {
        node {
          label 'EnginePSR272'
        }

      }
      steps {
        warnError(message: 'set unstable')
        node(label: 'DEV-812') {
          sh 'testing'
        }

        catchError(buildResult: 'pkay result', message: 'pkay msg', stageResult: '0')
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
        sh '''/e2open/bin/setup stop

/e2open/bin/setup start'''
      }
    }
    stage('Manual Verification Admin') {
      steps {
        input 'Verify Admin Logs and Confirm to proceed.'
      }
    }
  }
}