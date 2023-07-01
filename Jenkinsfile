pipeline {
    agent any

    stages {
        stage('Configure SSH') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'github-private-key', keyFileVariable: 'SSH_PRIVATE_KEY', passphraseVariable: '', usernameVariable: 'SSH_USERNAME')]) {
                    // Set the GIT_SSH_COMMAND variable
                    sh 'export GIT_SSH_COMMAND="ssh -i $SSH_PRIVATE_KEY"'

                    // Perform the git push command
                    sh 'git push git@github.com:halahakim119/softwreConsProject.git aTag'
                }
            }
        }
    }
}
