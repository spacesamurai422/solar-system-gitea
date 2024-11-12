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

        stage('Test') {
            steps {
                sh 'echo "Running test now"'
                sh 'node -v'
                sh 'npm -v'
            }
        }
    }
}
