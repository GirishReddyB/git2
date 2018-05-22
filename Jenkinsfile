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
    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("girish_mule_39/${env.BUILD_ID}")
    }
    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
       /*      app.push("${env.BUILD_NUMBER}") */
            app.push("latest")
        }
    }
    }
}