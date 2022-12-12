def runNewmanStage(collectionFileName, environmentFileName) {
  sh "newman run ./collections/${collectionFileName} -e ./collections/${environmentFileName}"
}

pipeline {
    agent any

    stages {
        stage('stage 1') {
            steps {
                // sh "newman run ./collections/Cloning-Disabled.postman_collection.json -e ./collections/environment.json"
              script {
                runNewmanStage("Cloning-Disabled.postman_collection.json", "environment.json")
               }
            }
        }
    }
}
