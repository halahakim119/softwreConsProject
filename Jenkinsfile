pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                jiraComment body: 'This is a comment by Jenkins', issueKey: 'KAN-2'
            }
        }

        stage('JMeter Performance Test') {
            steps {
                // Run JMeter test using the JMeter plugin
                script {
                    jmeter {
                        jmeterInstallation('Apache JMeter') // Configure JMeter installation name defined in Jenkins global tools configuration
                        jmx('C:/Users/msi-pc/OneDrive/Desktop/jenkins.io.jmx') // Path to your JMeter test script
                        flags('-Jjmeter.save.saveservice.output_format=xml') // Optional: Configure JMeter flags as needed
                        testArgs('-l C:/Program Files/jmeter/result.jtl') // Path to save JTL report file
                    }
                }
            }
        }
    }

    post {
        always {
            // Publish JMeter performance test report using the Performance Plugin
            step([$class: 'JUnitResultArchiver', testResults: 'C:/Program Files/jmeter/result.jtl']) // Path to the JTL report file
            step([$class: 'PerformancePublisher', parsers: [[$class: 'JUnitParser', glob: 'C:/Program Files/jmeter/result.jtl']]]) // Path to the JTL report file
        }
    }
}
