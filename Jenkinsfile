pipeline {
    agent any

    stages {
        stage('Configure SSH') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [[$class: 'CleanBeforeCheckout']], userRemoteConfigs: [[credentialsId: 'github-private-key', url: 'https://github.com/halahakim119/softwreConsProject.git']]])
            }
        }

        stage('Commit and Push') {
            steps {
                script {
                    gitCommit = sh(script: 'git log --format="%H" -n 1', returnStdout: true).trim()
                    sh 'git config user.email "your-email@example.com"'
                    sh 'git config user.name "Your Name"'
                    sh 'git add .'
                    sh 'git commit -m "Pipeline commit"'
                    sh 'git push origin main'
                }
            }
        }

    
    }
}
