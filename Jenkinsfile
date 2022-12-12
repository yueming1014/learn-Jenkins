// def runNewmanStage(collectionFile, environmentFile) {
//   sh "newman run ./${collectionFile} -e ./${environmentFile}"
// }

pipeline {
    agent any

    stages {
        stage('stage 1') {
            steps {
                sh "newman run ./Cloning-Disabled.postman_collection.json -e ./environment.json"
            //   script {
            //     runNewmanStage("API 2.0 Perm Suite -- Cloning Disabled.postman_collection.json")
            //    }
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
