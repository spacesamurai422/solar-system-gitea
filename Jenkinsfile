pipeline {
    agent any
    tools {
        nodejs 'node-2260'
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo "Running build now"'
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
