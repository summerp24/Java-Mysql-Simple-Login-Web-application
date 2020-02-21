pipeline {
 	agent any
	wrap([$class: 'AnsiColorBuildWrapper', 'colorMapName': 'XTerm']) {
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
			    ansiColor('xterm') {
				    sh "docker images"
			    	    sh "docker build -t pdlwebapp:1.0 ."
			    }
		}
		}
		stage('docker_push') {
			steps {
			    sh "sudo docker tag pdlwebapp:1.0 summerp24/pdlwebapp:1.0"
				sh "sudo docker push summerp24/pdlwebapp:1.0"
		}
		}
		stage('container_up') {
			steps {
			    sh "docker run -itd --name webapp01 -p 8090:8080 pdlwebapp:1.0"
		}
		}
	}
}
}
