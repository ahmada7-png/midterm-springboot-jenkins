pipeline {
  agent any
  stages {
    stage('Checkout') { steps { checkout scm } }
    stage('Build') {
      steps { sh 'mvn -B clean package' }
      post { success { archiveArtifacts artifacts: 'target/*.jar', fingerprint: true } }
    }
  }
  post {
    always {
      junit '**/target/surefire-reports/*.xml'
      cleanWs()
    }
  }
}
