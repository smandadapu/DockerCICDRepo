pipeline {

 agent { label 'prod' }    //agent any


stages {
  stage(checkout)
   {
    steps 
	  {
	   git 'https://github.com/smandadapu/DockerCICDRepo.git'
	   
	   checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/smandadapu/DockerCICDRepo.git']]])
	  }
   
   }
   
   stage(build)
   {
    steps 
	  {
	    bat "mvn -Dmaven.test.failure.ignore=true clean install"
	    bat "mvn sonar:sonar -Dsonar.login="
	  }
   
   }
   post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    archiveArtifacts 'target/*.war'
                }
            }

}




}