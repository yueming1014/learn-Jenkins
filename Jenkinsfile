def runNewmanStage(collectionFileName, environmentFileName) {
  sh "newman run ./collections/${collectionFile} -e ./collections/${environmentFile}"
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
    // stages {
    //     stage('stage 2') {
    //         steps {
    //         //   script {
    //         //     runNewmanStage("API 2.0 Perm Suite -- FCS Files Only - View Only.postman_collection.json")
    //         //    }
    //         }
    //     }
    // }
}
