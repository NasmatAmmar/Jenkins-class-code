pipeline {
	agent any

	stages {
		stage('build') {
			steps {
				sh '''
					echo "Build stage" > app.txt
				'''
			}
		}

		stage('test') {
			steps {
				sh '''
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
