pipeline {
    agent any

    stages {
        stage('Configure SSH') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'github-private-key', keyFileVariable: 'SSH_PRIVATE_KEY', passphraseVariable: '', usernameVariable: 'SSH_USERNAME')]) {
                    script {
                        sh('git tag -a some_tag -m "Jenkins"')
                        sh('git push <REPO> --tags')
                    }
                }
            }
        }
    }
}
