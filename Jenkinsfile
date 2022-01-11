pipeline{
	agent any     //{label 'docker-slave'}
	environment {
		DOCKERHUB_CREDENTIALS=credentials('Dockerhub')
	        }

	stages {
	    stage('Build') {
			steps {
				sh 'docker build -t kranthi5121/maven:latest .'
			    }
		}
		stage('Login') {
			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			    }
		}
		stage('Push') {
			steps {
				sh 'docker push kranthi5121/maven:latest'
			      }
		}
	}
	post {
		always {
			sh 'docker logout'
		    }
	}
}
