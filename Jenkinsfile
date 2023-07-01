pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                jiraComment body: 'this comment was sent from Jenkins', issueKey: 'KAN-2'
            }
        }
    }
}
