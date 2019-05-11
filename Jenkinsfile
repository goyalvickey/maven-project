pipeline{
  agent any
    stages{
      stage('SCM checkout'){
        git 'https://github.com/goyalvickey/maven-project.git'
      }
	  stage('maven test'){
	    steps{
		  withMaven(maven: 'Local_Maven'){
		    sh 'mvn test'
		  }
		}
	  }
	  stage('maven package'){
	    steps{
		  withMaven(maven: 'Local_Maven'){
		    sh 'mvn package'
		  }
		}
	  }
	  stage('maven install'){
		steps{
		  withMaven(maven: 'Local_Maven'){
		    sh 'mvn install'
		  }
		}
	  }
  }
}
