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
			    sh "docker images"
			    sh "docker build -t mtwebapp:2.0 ."
   	        }
		}
		stage('docker_push') {
			steps {
			    sh "sudo docker tag mtwebapp:2.0 milindtech/mtwebapp:2.0"
				sh "sudo docker push milindtech/mtwebapp:2.0"
   	        }
		}
		stage('container_up') {
			steps {
			    sh "docker run -itd --name webapp01 -p 8090:8080 mtwebapp:2.0"
   	        }
		}
	}
}
