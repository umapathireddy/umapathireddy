pipeline {
  agent {
    docker {
      image 'maven:3.39-jdk-8'
      args 'C:\\Users\\kumar\\.m2'
    }

  }
  stages {
    stage('inst') {
      steps {
        sh '''echo PATH = $PATH
echo M2_HOME =${M2_HOME}
mvn clean'''
      }
    }
    stage('build') {
      steps {
        sh 'mvn -dmaven.test.failure.ignore=true install'
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