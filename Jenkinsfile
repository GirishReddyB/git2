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
        
		             stage("Build App") {
		               agent any 
		               steps { buildimage() }
		           }
   
   
   
		       }
		   }
  
		   // ================================================================================================
		   // Build steps
		   // ================================================================================================

		   def buildimage() {
		       def buildResult
   
		           echo "Connect to registry at ${env.REGISTRY_URL}"
		           dockerRegistryLogin()
		           echo "Build ${env.IMAGE_NAME}"
		           buildResult = docker.build(Mule_App/hellonode)
		           echo "Register ${env.IMAGE_NAME} at ${env.REGISTRY_URL}"
  
		           echo "echo image"
		           sh "docker image ls"
		       
		   }