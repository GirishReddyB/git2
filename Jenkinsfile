pipeline {
  agent any
  stages {
    stage('Build Maven') { 
      steps {
      withMaven( maven : 'maven_3.5.3_1'){
        sh 'mvn install'
        }
      }
    }
    stage('Deploy Standalone') { 
      steps {
      withMaven( maven : 'maven_3.5.3_1'){
        sh 'mvn deploy -P standalone'
      }
      }
    }
    }
}