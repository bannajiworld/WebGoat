pipeline {
    agent any

    environment {
        SCANCENTRAL_CMD = "/opt/Fortify/Fortify_SCA_24.4.0/bin/scancentral"
        SSC_URL = "http://192.168.20.18:8080/ssc"
        SSC_TOKEN = "8b1b84d4-3ed9-40de-aac7-de850ca254d3"
        UPTOKEN = "8b1b84d4-3ed9-40de-aac7-de850ca254d3"
        APPLICATION_NAME = "Simple Maven Project"
        VERSION_ID = "10001"
        BUILD_TOOL = "/home/internal/jenkins/apache-maven-3.9.9/bin/mvn"
        BUILD_FILE = "pom.xml"
    }

    stages {
        stage('Fortify Scan') {
            steps {
                script {
                    try {
                        sh '''
                        echo "Starting Fortify Scan..."
                        ${SCANCENTRAL_CMD} -sscurl ${SSC_URL} -ssctoken ${SSC_TOKEN} \
                        start -upload -application "${APPLICATION_NAME}" -versionid ${VERSION_ID} \
                        -uptoken ${UPTOKEN} -bt ${BUILD_TOOL} -bf ${BUILD_FILE}
                        '''
                    } catch (Exception e) {
                        echo "Error during Fortify scan: ${e}"
                        error("Fortify Scan failed!")
                    }
                }
            }
        }
    }
}
