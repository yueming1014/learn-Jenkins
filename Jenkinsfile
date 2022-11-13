pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('run a collection') {
            steps {
                sh "newman run .\collections\runNewmanExample.postman_collection.json"
            }
        }
    }
}