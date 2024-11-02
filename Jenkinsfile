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
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'  // Path to your JUnit reports
        }
    }
}
