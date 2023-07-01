pipeline {
    agent any

    stages {
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
