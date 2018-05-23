pipeline {
   agent any
  stages {
    stage('Build Maven') { 
      steps {
      withMaven( maven : 'maven_3_5_3'){
        sh 'mvn install'
        }
        }
        
        
        stage('Build image') {
		        /* This builds the actual image; synonymous to
		         * docker build on the command line */
	         
	      

			steps {
		       sh 'docker build -t girish_mule_39:latest -f Dockerfile3 .' 
		      /*  app = docker.build("getintodevops/hellonode") */
		      }
		   }
      }
      
    }
}