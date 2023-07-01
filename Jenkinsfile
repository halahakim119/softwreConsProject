pipeline {
    agent any

    stages {
        stage('Configure SSH') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'github-PAT', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        sh("git tag -a some_tag -m 'Jenkins'")
                        sh("git push https://${GIT_USERNAME}:${GIT_PASSWORD}@<REPO> --tags")
                    }
                }
            }
        }
    }
}
