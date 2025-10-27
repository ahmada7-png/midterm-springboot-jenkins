pipeline {
  agent {
    docker {
      image 'maven:3.9.6-eclipse-temurin-11'
      args '-v $HOME/.m2:/root/.m2'
    }
  }

  stages {
    stage('Build') {
      steps {
        sh 'mvn -B clean package'
      }
      post {
        success {
          archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
      }
    }
  }
}
