pipeline {
   agent any
  stages {
    stage('Build Maven') { 
      steps {
      withMaven( maven : 'maven_3_5_3'){
        sh 'mvn install'
        }
        }
        
        
   
    }
}