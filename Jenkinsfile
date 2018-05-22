pipeline {
  agent any
  stages {
    stage('Build Maven') { 
      steps {
      withMaven( maven : 'maven_3.5.3_1'){
        sh 'mvn intsall'
        }
      }
    }
    stage('Deploy Standalone') { 
      steps {
        sh 'mvn deploy -P standalone'
      }
    }
    }
}