pipeline {
    agent any

    stages {
        stage('Run the tests') {
            steps {
                sh './mvnw clean test -X'  // Run tests with debug output
            }
        }
    }

    post {
        always {
            script {
                // List the contents of the workspace for debugging
                sh 'ls -R'  // Show all files and directories
            }
            junit 'target/surefire-reports/*.xml'  // Publish JUnit test results
        }
    }
}
