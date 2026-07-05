pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo '========== BUILD =========='

                sh '''
                python3 -m pip install --upgrade pip
                pip3 install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo '========== TEST =========='

                sh '''
                pytest
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo '========== DEPLOY =========='

                sh '''
                echo "Deploying application to staging..."
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