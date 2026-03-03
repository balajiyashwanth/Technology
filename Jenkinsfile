pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        dir('FDM') { sh 'echo Building FDM' }
        dir('MDM') { sh 'echo Building MDM' }
      }
    }
  }
}
