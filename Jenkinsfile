def runNewmanStage(collectionFileName, environmentFileName) {
  sh "newman run ./collections/${collectionFileName} -e ./collections/${environmentFileName}"
}

pipeline {
    agent any

    stages {
        stage('stage 1') {
            steps {
              script {
                runNewmanStage("Cloning-Disabled.postman_collection.json", "environment.json")
               }
            }
        }
    }
}
