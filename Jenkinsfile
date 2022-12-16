def runOneCollection(collectionFileName, environmentFileName) {
  sh "newman run ./collections/${collectionFileName} -e ./collections/${environmentFileName} --reporters cli htmlextra,junit --reporter-htmlextra-export newman/report.html --reporter-junit-export newman/report.xml"
}

pipeline {
  agent any

  options { timeout(time: 15, unit: 'MINUTES') }

  // triggers {
  //   cron(0 8 * * 1-5)
  // }

  environment {
    ENVIRONMENT_FILE_NAME="Environment-Variables.json"

    EMAILLIST="wqin@beckman.com" 

    STAGE_ADVANCED_ANALYSIS="Advanced-Analysis.postman_collection.json"
    STAGE_CLONING_DISABLED_VIEW_ONLY="Cloning-Disabled-View Only DS.postman_collection.json"
    STAGE_CLONING_DISABLED="Cloning-Disabled.postman_collection.json"
    STAGE_DATA_SERVICE="Data-Service.postman_collection.json"
    STAGE_FCS_FILE_ILLUSTRATIONS_DS="FCS-files-Illustrations DS.postman_collection.json"
    STAGE_FCS_FILES_ONLY_VIEW_ONLY="FCS-Files-Only-View Only.postman_collection.json"
    STAGE_FULL_CLONE_ILLUSTRATIONS_DS="Full-Clone-Illustrations DS.postman_collection.json"
    STAGE_FULL_CLONE_ILLUSTRATIONS="Full-Clone-Illustrations.postman_collection.json"
    STAGE_FULL_CLONE_VIEW_ONLY_DS="Full-Clone-View Only DS.postman_collection.json"
    STAGE_TEST="demo.json"
  }
  
  stages {
    stage('Advanced Analysis') {
      steps {
        // runOneCollection("${STAGE_TEST}", "${ENVIRONMENT_FILE_NAME}")
        sh "newman run ./collections/${STAGE_TEST} --reporters cli,htmlextra --reporter-htmlextra-export newman/"
      }
    }
  }

  post {
    always {
      // archiveArtifacts artifacts: "${env.WORKSPACE}/newman/report.html", followSymlinks: false
      archiveArtifacts artifacts: "newman/report.html", followSymlinks: false
      emailext (
        to: "${EMAILLIST}",
        subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
        body: "pls pay attention to API test results."
      )
    }
  }
}
