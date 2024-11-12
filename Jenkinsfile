pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Running build now"'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Running test now"'
                sh '/opt/homebrew/bin/node -v'
                sh '/opt/homebrew/bin/npm -v'
            }
        }
    }
}
