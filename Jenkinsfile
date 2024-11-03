pipeline {
    agent any

    stages {
        stage('Run the tests') {
            steps {
                bat './mvnw clean test -DsuiteXmlFile=testng.xml -X'  // Run tests with TestNG
            }
        }
    }

    post {
        always {
            script {
                // List the contents of the workspace for debugging
                bat 'dir' // Show all files and directories
            }
            junit 'target/surefire-reports/*.xml'  // Publish JUnit test results
        }
    }
}
