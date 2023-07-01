pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-credential-hla', url: 'https://github.com/halahakim119/softwreConsProject.git'
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Commit and Push') {
            steps {
                sh '''
                    git add .
                    git commit -m "Commit message"
                    git push origin main
                '''
            }
        }

        stage('Hello') {
            steps {
                jiraComment body: 'this comment was sent from Jenkins', issueKey: 'KAN-2'
            }
        }
    }
}
