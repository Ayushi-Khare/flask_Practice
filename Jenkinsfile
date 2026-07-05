pipeline {
    agent any

    environment {
        MONGO_URI = 'mongodb+srv://admin:HeroVired1234@jenkins.chwh8rm.mongodb.net/studentdb?retryWrites=true&w=majority&appName=Jenkins'
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

        echo "Installing dependencies..."
        pip3 install --break-system-packages -r requirements.txt

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
    always {
        echo 'Pipeline Finished.'
    }

    success {
        echo 'Pipeline Successful!'
        emailext(
            to: 'ayushikhare2627@gmail.com',
            subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: """
The Jenkins build completed successfully.

Job: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Build URL: ${env.BUILD_URL}

Status: SUCCESS
"""
        )
    }

    failure {
        echo 'Pipeline Failed!'
        emailext(
            to: 'YOUR_EMAIL@gmail.com',
            subject: "FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: """
The Jenkins build has failed.

Job: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Build URL: ${env.BUILD_URL}

Status: FAILURE
"""
        )
    }
}
}