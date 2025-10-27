pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        sh 'chmod +x mvnw || true'
        sh './mvnw -B clean package'
      }
      post {
        success {
          archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
      }
    }
  }
}
