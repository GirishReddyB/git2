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
        
        stage('Build Image') { 
      steps {
     	
     	
	     	withDocker( docker : 'Docker_23'){
	     	 sh 'docker build -t girish_mule_39:v3 -f Dockerfile3 .' 
     	
     	}
        }
        }
        
   
    }
}