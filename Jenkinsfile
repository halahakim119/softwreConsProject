pipeline {
    agent any

   stages {
    stage('Configure SSH') {
        steps {
            checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-private-key', url: 'https://github.com/halahakim119/softwreConsProject.git']])
        }
    }

    stage('Commit and Push') {
        steps {
            // Add the changed files to the git index
            sh 'git add .'

            // Commit the changes with a commit comment
            sh "git commit -m 'this is first commit'"

            // Push the changes to the remote repository
            sh 'git push origin main'
        }
    }
}

}
