pipeline {
    agent any

    stages {
        stage('Environment Check') {
            steps {
                echo 'Checking Jenkins environment...'

                sh '''
                pwd
                ls -la
                python3 --version || python --version
                pip3 --version || pip --version
                '''
            }
        }
    }
}