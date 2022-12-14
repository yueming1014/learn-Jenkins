pipeline {
    agent any

   environment {
      EMAILLIST="wqin@beckman.com" 
    }
  
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }

    post {
      always {
        emailext (
          to: "${EMAILLIST}",
          subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}",
          body: "pls pay attention to API test results."
        )
      }
    }
}