pipeline {
    agent any

    stages {
        stage('Configure SSH') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'github-private-key', keyFileVariable: 'SSH_PRIVATE_KEY', passphraseVariable: '', usernameVariable: 'SSH_USERNAME')]) {
                    sh 'git commit -am "hello my commit message"'
                    sh 'GIT_SSH_COMMAND="ssh -i $key"'
                    sh 'git push git@bitbucket.psr.io/scme/ci/ci.git aTag'
                }
            }
        }
    }
}
