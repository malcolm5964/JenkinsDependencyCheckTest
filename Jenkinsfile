pipeline {
	agent any

    stages {
        stage('OWASP Dependency-Check Vulnerabilities') {
            steps {
                    dependencyCheck additionalArguments: ''' 
                                -o './'
                                -s './'
                                -f 'ALL' 
                                --prettyPrint
                                --suppression suppression.xml''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
                
                dependencyCheckPublisher pattern: 'dependency-check-report.xml'
            }
        }
    }	

	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}