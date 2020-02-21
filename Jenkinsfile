pipeline {
 	agent any
	tools {
		maven 'Maven3.6.3'
		jdk 'Java8'
	}
	stages {
		stage('Build') {
			steps {
			    sh "ls -ltr"
				sh "mvn clean install package"
   	        }
		}
	}
}
