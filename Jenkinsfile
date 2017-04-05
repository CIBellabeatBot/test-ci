pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Build and Test') {
      steps {
        sh './gradlew clean build'
      }
    }
    stage('Record test results and artifacts') {
      steps {
        sh './gradlew uploadArchives'
        step([$class: 'ArtifactArchiver', artifacts: '**/repos/*.jar', fingerprint: true])
        step([$class: 'JUnitResultArchiver', testResults: '**/build/test-results/TEST-*.xml'])
      }
    }
  }
}
