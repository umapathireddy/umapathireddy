pipeline {
  agent none
  stages {
    stage('inst') {
      steps {
        sh '''echo PATH = $PATH
echo M2_HOME =${M2_HOME}
mvn clean'''
      }
    }
    stage('report') {
      steps {
        junit 'target/surefire-reports/**/*.xml'
        archiveArtifacts 'target/*.jar/target/*.hpi'
      }
    }
  }
}