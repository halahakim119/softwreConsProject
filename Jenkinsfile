pipeline {
    agent any

    stages {
        stage('Configure SSH') {
            steps {
                sshagent(credentials:['github-private-key']) {
                   
                }
            }
        }

        stage('Commit') {
            steps {
                sh 'git add .'
                sh 'git commit -m "Commit message"'
            }
        }

        stage('Push') {
            steps {
                sh 'git push origin main'
            }
        }
    }
}
