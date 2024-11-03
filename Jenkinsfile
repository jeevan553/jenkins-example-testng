pipeline {
    agent { label 'linux' } // Adjust based on your Jenkins setup

    stages {
        stage('Generate Sample Test Report') {
            steps {
                script {
                    // Create a sample testng-results.xml file with inline XML content
                    def xmlContent = '''<?xml version="1.0" encoding="UTF-8"?>
                    <!DOCTYPE suite SYSTEM "https://testng.org/testng-1.0.dtd">
                    <suite name="Sample Suite">
                        <test name="Sample Test">
                            <classes>
                                <class name="com.example.SampleTest"/>
                            </classes>
                        </test>
                    </suite>
                    <report xmlns="http://maven.apache.org/plugins/maven-surefire-plugin/report/1.0">
                        <test-case name="SampleTest.testMethod1" classname="com.example.SampleTest" time="0.002" status="PASS">
                            <reporter output="SampleTest Output"/>
                        </test-case>
                        <test-case name="SampleTest.testMethod2" classname="com.example.SampleTest" time="0.003" status="FAIL">
                            <reporter output="SampleTest Output"/>
                            <failure message="Expected condition failed" type="java.lang.AssertionError">
                                <![CDATA[Expected value was not equal to actual value]]>
                            </failure>
                        </test-case>
                    </report>'''

                    // Write the XML content to a file
                    writeFile(file: 'target/surefire-reports/testng-results.xml', text: xmlContent)
                }
            }
        }

        stage('Publish Test Results') {
            steps {
                // Publish the generated testng-results.xml file
                junit 'target/surefire-reports/testng-results.xml'
            }
        }
    }
}
