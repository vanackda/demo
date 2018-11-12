pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }

        stage('Dependency Check') {
            steps {
                dependencyCheckAnalyzer(datadir: '', hintsFile: '', includeCsvReports: false, includeHtmlReports: false, includeJsonReports: false, includeVulnReports: false, isAutoupdateDisabled: false, outdir: '${env.WORKSPACE}/build/reports/', scanpath: '${env.WORKSPACE}/', skipOnScmChange: false, skipOnUpstreamChange: false, suppressionFile: '', zipExtensions: '')
            }
        }    

        stage('Publish Reports') {
            steps {
                dependencyTrackPublisher(artifact:'build/reports/dependency-check-report.xml', artifactType: 'scanResult', projectName: 'demo', projectVersion:'1.0')            
            }
        }
    }
}
