pipeline {
  agent any
  def app
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
    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

         app = docker.build("girish_mule_39/${env.BUILD_ID}")
    }
    
    }
}