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
      
    
    // some block
	
	
	  stage('Build image') {
	        /* This builds the actual image; synonymous to
	         * docker build on the command line */
	         
	         dockerNode(credentialsId: '', dockerHost: 'tcp://192.168.99.100:2376', image: '', remoteFs: '') { 
	         }

		steps {
	       /* sh 'docker build -t shanem/spring-petclinic:latest .' */
	       app = docker.build("getintodevops/hellonode")
	      }
	   }
	
	
	
	
      
        
    }
}