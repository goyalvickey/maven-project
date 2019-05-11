pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/prakashk0301/maven-project'
        }
    }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn install'
                }
            }
        }
		
		stage('deply to tomcat') {
			steps {
				sshagent(['f9dbc14e-b0c0-4766-993f-4a5e1750caf2']) {
					sh 'ssh -o StrictHostKeyChecking=no -l */target/*.war ec2-user@172.31.22.77 uname -a'
				}
			}
		}
	}
}
