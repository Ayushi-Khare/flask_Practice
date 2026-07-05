pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo '========== BUILD STAGE =========='

                bat 'python -m pip install --upgrade pip'
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo '========== TEST STAGE =========='

                bat 'pytest'
            }
        }

        stage('Deploy') {
            steps {
                echo '========== DEPLOY STAGE =========='

                echo 'Deploying Flask application to Staging Environment...'

                bat 'echo Deployment Successful'
            }
        }
    }

    post {

        success {
            echo 'Pipeline executed successfully.'
        }

        failure {
            echo 'Pipeline execution failed.'
        }

        always {
            echo 'Pipeline execution completed.'
        }
    }
}