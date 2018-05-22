pipeline {
  agent any

  stages {
    stage('Build Maven') { 
      steps {
      withMaven( maven : 'maven_3.5.3_1'){
        sh 'mvn install'
        }
      }
      
      
      stage('Build image') {
	        /* This builds the actual image; synonymous to
	         * docker build on the command line */
	agent any
	
	steps {
        sh 'docker build -t shanem/spring-petclinic:latest .'
      }
	   
   }
    
    }
}