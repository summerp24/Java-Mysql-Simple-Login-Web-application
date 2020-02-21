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
		stage("\033[1;32m Build Source \033[0m") {
			steps {
			    sh "ls -ltr"
				sh "mvn clean install package"
			}
		}
		stage("\033[1;32m Build Docker Image \033[0m") {
			steps {
				script{
					sh "docker images"
					sh(
						script: 'docker build -t pdlwebapp:1.0 .',
						returnStdout: true
					).trim()
				}
			}
		}
		stage("\033[1;32m Push Image to Dockerhub \033[0m") {
			steps {
			    
				script {
					sh "sudo docker tag pdlwebapp:1.0 summerp24/pdlwebapp:1.0"
					try{
						sh "sudo docker push summerp24/pdlwebapp:1.0"
						sh "docker rmi summerp24/pdlwebapp:1.0"
					}catch{
						echo "could not push or remove image"
					}
				}
			}
		}
		stage("\033[1;32m Run Container \033[0m") {
			steps {
			    sh "docker run -itd --name webapp01 -p 8090:8080 pdlwebapp:1.0"
			}
		}
	}
}
