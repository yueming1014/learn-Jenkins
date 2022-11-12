pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World!!! happy everyday'
            }
        }
    }
    stages {
        stage('setup') {
            steps {
                sh "npm install -g newman"
            }
        }
    }
}