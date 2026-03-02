pipeline {
    agent { label 'aws-agent' }
    stages {
        stage('Test') {
            steps {
                sh 'hostname'
                sh 'free -h'
            }
        }
    }
}
