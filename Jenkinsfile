pipeline {
    agent any

    stages {

        stage('Check Python Environment') {
            steps {
                sh '''
                echo "===== Python ====="
                which python3 || true
                python3 --version || true

                echo "===== Pip ====="
                which pip3 || true
                pip3 --version || true

                echo "===== Pytest ====="
                which pytest || true
                pytest --version || true

                echo "===== Installed Packages ====="
                pip3 list || true
                '''
            }
        }
    }
}