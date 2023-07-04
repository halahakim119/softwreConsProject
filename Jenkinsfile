pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                jiraComment body: 'this is a comment by Jenkins', issueKey: 'KAN-2'
            }
        }

        post {
    always {
      // Publish JMeter performance test report using the Performance Plugin
      performanceReport parsers: [[$class: 'JMeterParser', glob: 'C:/Program Files/jmeter/result.jtl']] // Path to the JTL report file
    }
  }
    }
}
pipeline {
    agent any

    stages {
        stage('jmeter') {
            steps {

                // Run JMeter test using the JMeter plugin
                jmeter {
                    jmeterInstallation('Apache JMeter') // Configure JMeter installation name defined in Jenkins global tools configuration
                    jmx('C:/Users/msi-pc/OneDrive/Desktop/jenkins.io.jml.jmx') // Path to your JMeter test script
                    properties([
                        jtlReports('C:/Program Files/jmeter/result.jtl') // Path to save JTL report file
                    ])
                }
            }
        }

        stage('Hello') {
            steps {
                jiraComment body: 'this is a comment by Jenkins', issueKey: 'KAN-2'
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
