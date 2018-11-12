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

        stage('Dependency Check') {
            steps {
                dependencyCheckAnalyzer(datadir: '', hintsFile: '', includeCsvReports: false, includeHtmlReports: false, includeJsonReports: false, includeVulnReports: false, isAutoupdateDisabled: false, outdir: '/build/reports/', scanpath: '/', skipOnScmChange: false, skipOnUpstreamChange: false, suppressionFile: '', zipExtensions: '')
            }
        }    

        stage('Publish Reports') {
            steps {
                dependencyTrackPublisher(artifact:'build/reports/dependency-check-report.xml', artifactType: 'scanResult', projectName: 'demo', projectVersion:'1.0')            
            }
        }
    }
}
