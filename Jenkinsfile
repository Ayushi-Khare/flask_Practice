pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo '========== BUILD =========='

                sh '''
                python3 --version
                pip3 list
                '''
            }
        }

        stage('Test') {
            steps {
                echo '========== TEST =========='

                sh '''
                python3 -m pytest
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo '========== DEPLOY =========='

                sh '''
                echo "Deploying Flask application to Staging..."
                '''
            }
        }
    }

    post {

        success {
            echo 'Pipeline Successful!'
        }

        failure {
            echo 'Pipeline Failed!'
        }

        always {
            echo 'Pipeline Finished.'
        }
    }
}