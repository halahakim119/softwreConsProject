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
        stage('Build, Test, and Package') {
            steps {
                dir('jmeter') {
                    sh "./mvnw clean install -DskipTests"
                    sh 'nohup ./mvnw spring-boot:run -Dserver.port=8989 &'
                    sh "while ! httping -qc1 http://localhost:8989 ; do sleep 1 ; done"
                    sh "jmeter -Jjmeter.save.saveservice.output_format=xml -n -t src/main/resources/JMeter.jmx -l src/main/resources/JMeter.jtl"
                    step([$class: 'ArtifactArchiver', artifacts: 'JMeter.jtl'])
                    sh "pid=\$(lsof -i:8989 -t); kill -TERM \$pid || kill -KILL \$pid"
                }
            }
        }

         stage('Hello') {
            steps {
               jiraComment body: 'this is comment by jenkins', issueKey: 'KAN-2'
            }
        }
    }

 
}
