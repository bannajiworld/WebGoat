pipeline {
    agent any
    stage('Fortify Scan') {
            steps {
                sh '''
                    /opt/Fortify/Fortify_SCA_24.4.0/bin/scancentral -sscurl http://192.168.20.18:8080/ssc -ssctoken 8b1b84d4-3ed9-40de-aac7-de850ca254d3 start -upload -application "Simple Maven Project" -version 1 -bt mvn -bf pom.xml
                '''
            }
        }
}
