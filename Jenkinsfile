pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                jiraComment body: 'this is a comment by Jenkins', issueKey: 'KAN-2'
            }
        }

        stage('Execute JMeter') {
            steps {
                bat '''
                c:\
                jmeter\bin\jmeter -j imeter save saveservice output_format=xm] -n -t
                c:\
                limeter\bin\jenkins. io.inx -1 c:\
                imeter\reports\jenkins.
                io.report itl
                '''
            }
        }
        
        stage('Publish JMeter Report') {
            steps {
                perfReport filterRegex: '', sourceDataFiles: 'TestPlans/MyRun1.jtl'
            }
        }
    }
}
