node {
  stage 'Build and Test'
  checkout scm
  sh './gradlew build'
  stage 'Record test results and artifacts'
  sh './gradlew uploadArchives'
  step([$class: 'ArtifactArchiver', artifacts: '**/repos/*.jar', fingerprint: true])
  step([$class: 'JUnitResultArchiver', testResults: '**/build/test-results/TEST-*.xml'])
}
