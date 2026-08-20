pipeline {
	agent any

	environment {
		APP_VERSION = '1.0'
		APP_NAME = 'Jenkins-class-code'
		DOCKER_REPO = ''
	}

	stages {
		stage('build') {
			steps {
				sh '''
					echo "APP_VERSION=$APP_VERSION"
					echo "APP_NAME=$APP_NAME"
					echo "DOCKER_REPO=$DOCKER_REPO"
					echo "Build stage" > app.txt
				'''
			}
		}

		stage('test') {
			steps {
				sh '''
					echo "Pipeline name: $JOB_NAME"
					echo "Build number: $BUILD_NUMBER"

					if [ -f app.txt ]; then
						echo "app.txt exists"
					else
						echo "app.txt does not exist"
						exit 1
					fi
				'''
			}
		}

		stage('deploy') {
			steps {
				sh '''
					mkdir -p deploy
					cp app.txt deploy/
					ls -l deploy
				'''
			}
		}
	}

	post {
		always {
			cleanWs()
		}
	}
}
