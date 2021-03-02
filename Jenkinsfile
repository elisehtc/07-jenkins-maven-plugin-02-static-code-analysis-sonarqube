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
    		sh "mvn clean verify sonar:sonar -Dsonar.host.url=http://host.docker.internal:9000 -Dsonar.projectKey=07-static-code-analysis-sonarqube -Dsonar.projectVersion=$BUILD_NUMBER";
		  }
	  }
    }
  }