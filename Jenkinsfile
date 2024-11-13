pipeline {
    agent any
    tools {
        nodejs 'node-2260'
    }
    stages {
        stage('Installing Dependencies') {
            steps {
                sh 'npm install --no-audit'
            }
        }
        stage('NPM Dependency Audit') {
            steps {
                dependencyCheck additionalArguments: '''
                --scan \'./\'
                --out \'./\'
                --format \'ALL\'
                --prettyPrint''', odcInstallation: 'owasp-check-10'
            }
        }
    }
}
