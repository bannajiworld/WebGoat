pipeline {
    agent any
    stages {
        stage('Fortify Scan') {
            steps {
                fortifyRemoteAnalysis remoteAnalysisProjectType: fortifyMaven(buildFile: 'pom.xml'), uploadSSC: [appName: 'Simple Maven Project', appVersion: '1']
            }
        }
    }
}
