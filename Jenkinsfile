pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-cred')
    }

    tools {
        nodejs "nodejs"
        dockerTool "Default Docker"
    }

    stages {
        stage('Hello') {
            steps {
                jiraComment body: 'this is comment by jenkins', issueKey: 'KAN-2'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Docker Purne') {
            steps {
                sh 'docker image prune -af'
            }
        }

        stage('Docker build') {
            steps {
                sh 'docker build -t shevop/questionapp:latest .'
            }
        }

        stage('Docker login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u shevop -p $DOCKERHUB_CREDENTIALS_PSW'
            }
        }

        stage('Docker push') {
            steps {
                sh 'docker push shevop/questionapp:latest'
            }
        }

        stage('Execute JMeter') {
            steps {
                bat '''
                c: jmeter \\bin\\jmeter -j imeter save saveservice output_format=xm] -n -t
                c: limeter \\bin\\jenkins. io.inx -1 c: \\imeter\\ reports\\jenkins.
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

    post {
        always {
            sh 'docker logout'
        }
    }
}
