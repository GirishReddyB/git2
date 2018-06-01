  pipeline {
	
		      agent any
	  
		     stages {
			  
			    stage("Start Pipeline") {
		               steps { initialize() }
		           }   
			     
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
   			
			      //Clean docker container
			   stage("Clean docker container") {
		               steps {
				       script {
						try {
						      sh "docker stop mule_testapp"
						      sh "docker rm mule_testapp"
						  } catch (Exception ex) {

							echo "exception ::: ${ex}"

						  }
				       		}
			             }
		           }
			     
			     
   			 //Run Docker App
			   stage("Run Docker container") {
		               steps {
				  //   echo "Run APP Image ${env.IMAGE_NAME}"
				       
				       // docker.image("a_mule_app_test:").run("-p 9082:9082") 
				       
				       sh "docker run --name mule_testapp -p 9082:9082 -i -d a_mule_app_test:latest"
				       
				      // Sleep 10 SECONDS
				       //afterRunSleep()
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
			   buildResult = docker.build("${env.IMAGE_NAME}","-f ${dockerfile} ../Dev_Ops_Test/")
		         //  echo "Register ${env.IMAGE_NAME} at ${env.REGISTRY_URL}"
  
		           echo "echo image"
		           //sh "docker image ls"
		       
		   }
		   //Intialize

		def initialize() {
			
			  echo "***** Start - Setting Env Variables ******"
			    env.SYSTEM_NAME = "Girish_System"
			    //env.AWS_REGION = "us-east-1"
			    //env.REGISTRY_URL = "https://912661153448.dkr.ecr.us-east-1.amazonaws.com"
			    //env.MAX_ENVIRONMENTNAME_LENGTH = 32
			    //setEnvironment()
			    env.IMAGE_NAME = "a_mule_app_test" 
				//+ ((env.BRANCH_NAME == "master") ? "" : "${env.ENVIRONMENT}-") + 
				//env.BUILD_ID
			echo "**** Done - Setting Env Variables ******"
			    showEnvironmentVariables()
		}


		def showEnvironmentVariables() {
			    sh 'env | sort > env.txt'
			    sh 'cat env.txt'
		}

		def afterRunSleep(){
				def time = 10
		    echo "Waiting 10 seconds for deployment to complete prior starting smoke testing"
		    sleep time.toInteger() 

		}
