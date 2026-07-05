pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo '========== BUILD =========='

                sh '''
                python3 -m venv venv
                . venv/bin/activate

                python -m pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo '========== TEST =========='

                sh '''
                . venv/bin/activate

                pytest
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo '========== DEPLOY =========='

                sh '''
                echo "Deploying Flask Application to Staging..."
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