pipeline {
    agent any

    stages {
        stage('Configure SSH') {
            steps {
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-private-key', url: 'https://github.com/halahakim119/softwreConsProject.git']])
            }
        }

         stage('Hello') {
            steps {
                jiraComment body: 'this comment was sent from Jenkins', issueKey: 'KAN-2'
            }
        }

    
    }
}


