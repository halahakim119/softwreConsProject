pipeline {
    agent any

    stages {
        stage('Configure SSH') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[
                        credentialsId: 'github-private-key',
                        url: 'https://github.com/halahakim119/softwreConsProject.git'
                    ]]
                ])
            }
        }

        stage('Hello') {
            steps {
                echo 'Hello, World!'
            }
        }
    }

    triggers {
        githubPush()
    }
}
