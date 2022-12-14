def runOneCollection(collectionFileName, environmentFileName) {
  sh "newman run ./collections/${collectionFileName} -e ./collections/${environmentFileName}"
}

pipeline {
    agent any
  
    environment {
        STAGE_ADVANCED_ANALYSIS="Advanced-Analysis.postman_collection.json"
        ENVIRONMENT_FILE_NAME="Environment-Variables.json" 
    }

    stages {
        stage('Advanced Analyisis') {
            steps {
              script {
                runOneCollection(${STAGE_ADVANCED_ANALYSIS}, ${ENVIRONMENT_FILE_NAME})
               }
            }
        }
    }
}
