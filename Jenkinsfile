pipeline{

	agent {label 'linux'}

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/dennisbabu8/hello-python.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t  denni8/helloworld:tagname'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push denni8/helloworld:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
