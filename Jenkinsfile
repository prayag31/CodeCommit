pipeline {
  agent { label 'ec2-agent' }

  options { timestamps() }

  stages {
    stage('Checkout') {
      steps { checkout scm }
    }

    stage('Run') {
      steps {
        sh '''
          chmod +x app.sh
          ./app.sh | tee output.txt
        '''
      }
    }
  }

  post {
    always {
      archiveArtifacts artifacts: 'output.txt', fingerprint: true
    }
  }
}
