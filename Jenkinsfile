pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World!!! happy everyday'
            }
        }
        stage('setup') {
            steps {
                sh "npm install -g newman"
            }
        }
    }
}