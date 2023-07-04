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
                jmeter {
                    jmeterInstallation('Apache JMeter') // Configure JMeter installation name defined in Jenkins global tools configuration
                    jmx('C:/Users/msi-pc/OneDrive/Desktop/jenkins.io.jmx') // Path to your JMeter test script
                    properties([
                        jtlReports([
                            [pattern: 'C:/Program Files/jmeter/result.jtl'] // Path to save JTL report file
                        ])
                    ])
                }
            }
        }
    }

    post {
        always {
            // Publish JMeter performance test report using the Performance Plugin
            performanceReport parsers: [[$class: 'JMeterParser', glob: 'C:/Program Files/jmeter/result.jtl']] // Path to the JTL report file
        }
    }
}
