pipeline {
	agent any

    stages {
        stage('OWASP Dependency-Check Vulnerabilities') {
            steps {
                    dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default'
            }
        }
    }	

	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}