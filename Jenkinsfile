def runOneCollection(collectionFileName, environmentFileName) {
    catchError (
      buildResult: 'FAILURE',
      stageResult: 'FAILURE',
      catchInterruptions: false
    ) {
        sh "newman run ./collections/${collectionFileName} -e ./collections/${environmentFileName} -r cli,htmlextra,junit --reporter-htmlextra-export newman/${collectionFileName}/report.html --reporter-junit-export newman/${collectionFileName}/report.xml"
    }
}

pipeline {
  agent any

  options { timeout(time: 10, unit: 'MINUTES') }

  triggers {
    cron('0 8 * * 1-5')
  }

  environment {
    ENVIRONMENT_FILE_NAME="Environment-Variables.json"

    EMAILLIST="wqin@beckman.com yueming1014@126.com" 

    STAGE_Automatic_Gating="Automatic-Gating.postman_collection.json"
    STAGE_ADVANCED_ANALYSIS="Advanced-Analysis.postman_collection.json"
    STAGE_CLONING_DISABLED_VIEW_ONLY="Cloning-Disabled-View-Only-DS.postman_collection.json"
    STAGE_CLONING_DISABLED="Cloning-Disabled.postman_collection.json"
    STAGE_DATA_SERVICE="Data-Service.postman_collection.json"
    STAGE_FCS_FILE_ILLUSTRATIONS_DS="FCS-files-Illustrations-DS.postman_collection.json"
    STAGE_FCS_FILES_ONLY_VIEW_ONLY="FCS-Files-Only-View-Only.postman_collection.json"
    STAGE_FULL_CLONE_ILLUSTRATIONS_DS="Full-Clone-Illustrations-DS.postman_collection.json"
    STAGE_FULL_CLONE_ILLUSTRATIONS="Full-Clone-Illustrations.postman_collection.json"
    STAGE_FULL_CLONE_VIEW_ONLY_DS="Full-Clone-View-Only-DS.postman_collection.json"
    STAGE_TEST="demo.json"
  }
  
  stages {
    stage('Auto Gating') {
      steps {
          runOneCollection("${STAGE_Automatic_Gating}", "${ENVIRONMENT_FILE_NAME}")
      }
    }

    stage('Advanced Analysis') {
      steps {
          runOneCollection("${STAGE_ADVANCED_ANALYSIS}", "${ENVIRONMENT_FILE_NAME}")
      }
    }

    stage('Cloning Disabled View Only') {
      steps {
        runOneCollection("${STAGE_CLONING_DISABLED_VIEW_ONLY}", "${ENVIRONMENT_FILE_NAME}")
      }
    }

    stage('Cloning Disabled') {
      steps {
        runOneCollection("${STAGE_CLONING_DISABLED}", "${ENVIRONMENT_FILE_NAME}")
      }
    }

    stage('Data Service') {
      steps {
        runOneCollection("${STAGE_DATA_SERVICE}", "${ENVIRONMENT_FILE_NAME}")
      }
    }

    stage('Illustrations DS') {
      steps {
        runOneCollection("${STAGE_FCS_FILE_ILLUSTRATIONS_DS}", "${ENVIRONMENT_FILE_NAME}")
      }
    }

    stage('FCS Files Only View') {
      steps {
        runOneCollection("${STAGE_FCS_FILES_ONLY_VIEW_ONLY}", "${ENVIRONMENT_FILE_NAME}")
      }
    }

    stage('Full Clone Illustrations DS') {
      steps {
        runOneCollection("${STAGE_FULL_CLONE_ILLUSTRATIONS_DS}", "${ENVIRONMENT_FILE_NAME}")
      }
    }

    stage('Full Clone Illustrations') {
      steps {
        runOneCollection("${STAGE_FULL_CLONE_ILLUSTRATIONS}", "${ENVIRONMENT_FILE_NAME}")
      }
    }

    stage('Full Clone View Only DS') {
      steps {
        runOneCollection("${STAGE_FULL_CLONE_VIEW_ONLY_DS}", "${ENVIRONMENT_FILE_NAME}")
      }
    }
  }

  post {
    always {
      archiveArtifacts artifacts: "newman/**/report.html, newman/**/report.xml", followSymlinks: false
      emailext (
        to: "${EMAILLIST}",
        from: "yueming1014@126.com",
        subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
        body: "pls pay attention to API test results."
      )
    }
  }
}
