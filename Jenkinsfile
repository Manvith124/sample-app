properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '2', numToKeepStr: '2')), pipelineTriggers([pollSCM(ignorePostCommitHooks: true, scmpoll_spec: '* * * * *')])])

pipeline{
    agent any
    tools {
      maven 'Maven_Home.3.6.3'
    }

      stages {
        stage("scm_checkout") {
            steps {
              git credentialsId: 'github_id', url: 'https://github.com/githubjigalooru/maven-web-application.git'    
                
            }
	}
        stage ("build_artifact") {
  	  steps {
	    sh "mvn clean install"
	     }
  	
        }

     }
}
