pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git (url:'https://github.com/JoshuaLSE/JenkinsDependencyCheckTest', credentialsId: 'bubblegum_chewed')
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP Dependency Check'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
