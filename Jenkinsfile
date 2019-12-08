node ('master') {
  checkut scm
  state('Build') {
    withMaven(maven: 'M3') {
      if (isUnix()) {
        sh 'mvn -Dmaven.test.failure.ignore clean package'
      }
      else {
        bat 'mvn -Dmaven.test.failure.ignore clean package'
      }
    }
  }
  state('Results') {
    junit '**/target/surefire-reports/TEST-*.xml'
    archive 'target/*.jar'
  }
}
