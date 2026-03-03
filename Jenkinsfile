pipeline {
  agent any

  stages {

    stage('Build') {
      steps {
        dir('FDM') { sh 'echo Building FDM' }
        dir('MDM') { sh 'echo Building MDM' }
      }
    }

    stage('Test & Coverage') {
      steps {
        sh '''
          mkdir -p coverage
          echo "<?xml version='1.0'?>
          <coverage line-rate='0.85'></coverage>" > coverage/cobertura.xml
        '''
      }
    }

    stage('Publish Coverage') {
      steps {
        recordCoverage(
          tools: [[parser: 'COBERTURA', pattern: 'coverage/cobertura.xml']]
        )
      }
    }
  }
}
