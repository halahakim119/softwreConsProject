pipeline {
    agent any
    tools {
        nodejs "nodejs"
    }

    stages {
        stage('Install') {
            steps {
                git branch: 'main', url: 'https://github.com/halahakim119/softwreConsProject.git'
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/halahakim119/softwreConsProject.git'
                bat 'npm run build'
            }
        }

        stage('Test') {
            steps {
                git branch: 'main', url: 'https://github.com/halahakim119/softwreConsProject.git'
                bat 'npm run test'
            }
        }

        stage('Deploy') {
            steps {
                git branch: 'main', url: 'https://github.com/halahakim119/softwreConsProject.git'
                bat 'docker build -t calculatorreactappjenkins .'
                bat 'docker run -d -p 3000:3000 calculatorreactappjenkins'
            }
        }

        stage('Hello') {
            steps {
                jiraComment body: 'This is a comment by Jenkins', issueKey: 'KAN-2'
            }
        }

    }

    
}
