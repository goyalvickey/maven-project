pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/goyalvickey/maven-project.git'
        }

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
   }
}
