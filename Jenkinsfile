pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('ghada_access')
	}

	stages {
                stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		
		}

	        stage('Build') {

			steps {
				sh 'docker build -t ghadamu/ghada:latest .'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push ghadamu/ghada:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
