pipeline {
  agent { label 'linux' }
  stages {
       stage('Cleanup') {
            steps {
                // Delete the workspace
                cleanWs()
            }
        }
    stage('Run the tests') {
      steps {
        sh './mvnw clean test'
      }
    }
  }
  post {
    always {
      junit 'target/surefire-reports/*.xml'
    }
  }
}
