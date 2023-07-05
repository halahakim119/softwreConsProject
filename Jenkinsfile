pipeline {
    agent any
    tools {
        nodejs "nodejs"
    }

    stages {
        stage('Install') {
            steps {
                git 'https://github.com/halahakim119/softwreConsProject.git'
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                git 'https://github.com/halahakim119/softwreConsProject.git'
                bat 'npm run build'
            }
        }

        stage('Test') {
            steps {
                git 'https://github.com/halahakim119/softwreConsProject.git'
                bat 'npm run test'
            }
        }

        stage('Deploy') {
            steps {
                git 'https://github.com/halahakim119/softwreConsProject.git'
                bat 'docker build -t calculatorreactappjenkins .'
                bat 'docker run -d -p 3000:3000 reactappjenkins'
            }
        }

        stage('Hello') {
            steps {
                jiraComment body: 'This is a comment by Jenkins', issueKey: 'KAN-2'
            }
        }

        stage('JMeter Performance Test') {
            steps {
                script {
                    jmeter {
                        jmeterInstallation('Apache JMeter')
                        jmx('C:/Users/msi-pc/OneDrive/Desktop/jenkins.io.jmx')
                        flags('-Jjmeter.save.saveservice.output_format=xml')
                        testArgs('-l C:/Program Files/jmeter/result.jtl')
                    }
                }
            }
        }
    }

    post {
        always {
            step([$class: 'JUnitResultArchiver', testResults: 'C:/Program Files/jmeter/result.jtl'])
            step([$class: 'PerformancePublisher', parsers: [[$class: 'JUnitParser', glob: 'C:/Program Files/jmeter/result.jtl']]])
        }
    }
}
