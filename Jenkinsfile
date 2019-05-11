pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/goyalvickey/maven-project.git'
        }
    }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'Local_Maven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'Local_Maven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'Local_Maven') {
                    sh 'mvn install'
                }
            }
        }
		
	stage('deply to tomcat') {
		steps {
			sshagent(['a3c9973b-1e58-49f5-bfff-7fd85b3f8234']) {
			sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.22.77:/var/lib/tomcat/webapps/'
			}
		}
	}
}
}
