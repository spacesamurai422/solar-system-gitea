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

        stage('Dependency Scanning') {
            parallel {
                stage('NPM Dependency Audit') {
                    steps {
                        sh '''
                        npm audit --audit-level=critical
                        echo $?
                    '''
                    }
                }
                stage('OWASP Dependency check') {
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
    }
}
