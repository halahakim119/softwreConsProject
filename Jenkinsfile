pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                // Checkout the repository
                checkout scm
            }
        }
        stage('Build and Run') {
            steps {
                // Build and run the application
                bat 'start npm install' // Use the 'bat' step to execute Windows batch commands
                bat 'start npm run start'
            }
        }
    }
}
