pipeline {
    agent any
    
    tools {
        maven 'my-maven-3.6.3' 
    }
    
    stages {
    	 
	  // stage ('Clone') {
        //    steps {
          //      git branch: 'master', url: "https://github.com/elisehtc/07-jenkins-maven-plugin-02-static-code-analysis-sonarqube"
            //}
	    //}
	 
	  stage('Static Code Analysis'){
             	  steps {
             	        withSonarQubeEnv('my_sonarqube_in_docker') {
                          // Optionally use a Maven environment you've configured already
                           // withMaven(maven:'my-maven-3') {
             	      
             	             	sh "mvn clean verify sonar:sonar -Dsonar.host.url=http://host.docker.internal:9000   -Dsonar.projectName=07-static-code-analysis-sonarqube -Dsonar.projectKey=07-static-code-analysis-sonarqube -Dsonar.projectVersion=$BUILD_NUMBER";
                          //  }
             	        }   
             	  }
            }
               
            stage("Quality Gate") {
                  steps {
                      timeout(time: 1, unit: 'HOURS') {
                          // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                          // true = set pipeline to UNSTABLE, false = don't
                          waitForQualityGate abortPipeline: true
                      }
                  }
            }
    }
}
