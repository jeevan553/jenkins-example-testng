pipeline {
    agent { label 'linux' }  // Specify the agent label

    stages {
        stage('Build') {
            steps {
                // Your build commands here
                sh './mvnw clean package'  // Adjust as needed for your build process
            }
        }
        stage('Run the Tests') {
            steps {
                sh './mvnw clean test'  // Run your tests
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'  // Path to your JUnit reports
        }
    }
}
