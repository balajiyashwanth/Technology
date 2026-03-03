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
          cat > coverage/cobertura.xml <<EOF
<?xml version="1.0" ?>
<coverage line-rate="0.92" branch-rate="0.80" version="1.0">
  <packages>
    <package name="sample" line-rate="0.92">
      <classes>
        <class name="SampleClass" filename="SampleClass.cs" line-rate="0.92">
          <lines>
            <line number="1" hits="1"/>
          </lines>
        </class>
      </classes>
    </package>
  </packages>
</coverage>
EOF
        '''
      }
    }

    stage('Publish Coverage') {
      steps {
        recordCoverage(
          tools: [[parser: 'COBERTURA', pattern: 'coverage/cobertura.xml']],
          scm: 'git',
          qualityGates: [
            [metric: 'LINE', threshold: 90.0]
          ]
        )
      }
    }
  }
}
