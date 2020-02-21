pipeline {
 	agent any
	tools {
		maven 'Maven3.6.3'
		jdk 'Java8'
	}
	stages {
		stage('build_source') {
			steps {
			    sh "ls -ltr"
				sh "mvn clean install package"
   	        }
		}
		stage('docker_image') {
			steps {
			    sh "docker build -t mtwebapp:2.0 ."
   	        }
		}
		stage('docker_push') {
			steps {
			    sh "docker tag mtwebapp:2.0 milindtech/mtwebapp:2.0"
				sh "docker push milindtech/mtwebapp:2.0"
   	        }
		}
	}
}
