pipeline {
    agent { label 'linux' }  // Specify the agent label

    stages {
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
