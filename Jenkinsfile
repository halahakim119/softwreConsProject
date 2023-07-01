pipeline {
    agent any

    stages {
        stage('Configure SSH') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/master']],
                    userRemoteConfigs: [[credentialsId: 'github-private-key', url: 'https://github.com/halahakim119/softwreConsProject.git']],
                    extensions: [[$class: 'CleanBeforeCheckout']]
                ])
            }
        }
        stage('Build and Run') {
            steps {
                // Build and run the application
                bat 'start npm install' // Use the 'bat' step to execute Windows batch commands
                bat 'start npm run start'
            }
        }
        stage('Push to GitHub') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'github-private-key', keyFileVariable: 'SSH_KEY')]) {
                    bat 'git config --global user.email "hakimhala3@gmail.com"'
                    bat 'git add .'
                    bat 'git add -u' // Add modified/deleted files
                    bat 'git add -A' // Add untracked files
                    bat 'git commit -m "Jenkins pipeline commit"'
                    bat 'git push origin master' // Push changes to the master branch
                }
            }
        }
    }
}
