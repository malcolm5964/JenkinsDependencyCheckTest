pipeline {
	agent any

    stages {
        stage('OWASP DependencyCheck') {
            steps {
                withCredentials([string(credentialsId: 'nvd-api-key', variable: 'NVD_API_KEY')]) {
                    dependencyCheck additionalArguments: "--format HTML --format XML --nvdApiKey ${NVD_API_KEY}", odcInstallation: 'Default'
                }
            }
        }
    }	
	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}