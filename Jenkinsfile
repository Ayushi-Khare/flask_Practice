pipeline {
    agent any

    environment {
        MONGO_URI = 'mongodb+srv://admin:HeroVired2026@jenkins.chwh8rm.mongodb.net/studentdb?retryWrites=true&w=majority&appName=Jenkins'
        SECRET_KEY = 'HeroVired123'
    }

    stages {

        stage('Build') {
            steps {
                echo '========== BUILD =========='

                sh '''
                echo "Creating .env file..."

                cat > .env <<EOF
MONGO_URI=$MONGO_URI
SECRET_KEY=$SECRET_KEY
EOF

                echo "Contents of workspace:"
                ls -la

                python3 --version
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