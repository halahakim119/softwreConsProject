pipeline {
    agent any

    stages {
        stage('Configure SSH') {
            steps {
                script {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-private-key', url: 'https://github.com/halahakim119/softwreConsProject.git']])
                    sh '''
                        git add .
                        git commit -m "push to git"
                        git push origin main
                    '''
                }
            }
        }
    }
}
