  pipeline {
	
		      agent any
	  
		     stages {
			 //Test App  
			     stage("Test App") {
		               steps {
				     echo "App Testing success"
			             }
		           }
			     
			//Build Build App   
		       stage('Build App') { 
		         steps {
		         withMaven( maven : 'maven_3_5_3'){
		           sh 'mvn install'
		           }
		           }
		           }
			     
			     
        		//Build Docker Image
		            stage("Build Docker Image ") {
		               agent any 
		               steps { buildimage() }
		           }
   
   			 //Run Docker App
			   stage("Run Docker App") {
		               steps {
				     echo "Run APP Image ${IMAGE_NAME}"
			             }
		           }
			     
			     
   			//stages
		       }
		
	   //pipeline
	}
  
		   // ================================================================================================
		   // Build steps
		   // ================================================================================================

		   def buildimage() {
			    def dockerfile = 'Dockerfile3'
			   def IMAGE_NAME = 'a_mule_app_test'
		       def buildResult
   
		           echo "Connect to registry at ${env.REGISTRY_URL}"
		           
		           echo "Build ${env.IMAGE_NAME}"
		        //   buildResult = docker.build("a_mule_app_test","-f ${dockerfile} ../Dev_Ops_Test/")
			   buildResult = docker.build("${IMAGE_NAME}","-f ${dockerfile} ../Dev_Ops_Test/")
		           echo "Register ${env.IMAGE_NAME} at ${env.REGISTRY_URL}"
  
		           echo "echo image"
		           sh "docker image ls"
		       
		   }
