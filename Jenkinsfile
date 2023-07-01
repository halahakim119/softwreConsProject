pipeline {
    agent any

    stages {
        // stage('Hello') {
        //     steps {
        //         jiraComment body: 'this comment was sent from Jenkins', issueKey: 'KAN-2'
        //     }
        // }
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
