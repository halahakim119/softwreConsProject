pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from Git
                checkout scm
            }
        }
        stage('Build') {
            steps {
                // Perform your build steps here
                // For example:
                bat 'npm install'  // Run npm install using the Windows shell
                bat 'npm run build' // Run npm run build using the Windows shell
            }
        }
        stage('Run in Background') {
            steps {
                // Run your command in the background using the Windows 'start' command
                bat 'start /B cmd /C "your-command"'
            }
        }
    }
}
