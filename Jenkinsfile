
pipeline{

   agent any
	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}
	
	stages {

		stage('gitclone') {

		      steps {
		         git 'https://github.com/theitern/PublishImageToDockerhub.git'
		      }
		}
		
		stage('Build') {
			steps {
			
			   sh 'docker build -t akinaregbesola/class_app:latest .'
			}
		}
		
		stage('Login') {
		
			steps {
			   sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --passwd-stdin'
			}
		}

		stage('Push') {
			
			steps {
			   sh 'docker push akinaregbesola/class_app:latest'
			}
		}
		}
	
	post {
	    always {
		sh 'docker logout'
	    }
    }

}
