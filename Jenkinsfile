pipeline {
 	agent any
	tools {
		maven 'Maven3.6.3'
		jdk 'Java8'
	}
	options {
	    ansiColor('xterm')
	}
	stages {
		stage("\033[42m Build Source \033[0m") {
			steps {
			    sh "ls -ltr"
				sh "mvn clean install package"
		}
		}
		stage("\033[42m Build Docker Image \033[0m") {
			steps {
			    ansiColor('xterm') {
				    sh "docker images"
			    	    sh "docker build -t pdlwebapp:1.0 ."
			    }
		}
		}
		stage("\033[42m Push Image to Dockerhub \033[0m") {
			steps {
			    sh "sudo docker tag pdlwebapp:1.0 summerp24/pdlwebapp:1.0"
				sh "sudo docker push summerp24/pdlwebapp:1.0"
			}
		}
		stage("\033[42m Run Container \033[0m") {
			steps {
			    sh "docker run -itd --name webapp01 -p 8090:8080 pdlwebapp:1.0"
			}
		}
	}
}
