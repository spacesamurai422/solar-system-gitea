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
                    steps  {
                        dependencyCheck additionalArguments: '''
                    --scan \'./\'
                    --out \'./\'
                    --format \'ALL\'
                    --prettyPrint''', odcInstallation: 'owasp-check-10'
                        publishHTML([allowMissing: true, alwaysLinkToLastBuild: true, keepAll: true, reportDir: './', reportFiles: 'dependency-check-jenkins.html', reportName: 'Dependency check', reportTitles: '', useWrapperFileDirectly: true])
                        junit allowEmptyResults: true, keepProperties: true, stdioRetention: '', testResults: 'dependency-check-report.xml'
                    }
                }
            }
        }
    }
}
