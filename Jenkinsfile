pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }
        stage('OWASP Dependency Check') {
            steps {
                sh './gradlew dependencyCheckAnalyze'
            }
        }

	stage('Publish Reports') {
		steps {
			dependencyTrackPublisher(artifact:'build/reports/dependency-check-report.xml', artifactType: 'scanResult', projectName: 'demo', projectVersion:'1.0')            
		}
	}
    }
}
