pipeline {
    agent any

    environment {
        PYTHON = 'python3' // Change to 'python' if using Python 2
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout scm
                }
            }
        }

        stage('Setup Python') {
            steps {
                script {
                    sh "${PYTHON} --version"
                    sh "pip install --upgrade pip"
                    sh "pip install pylint" // Install pylint for linting
                }
            }
        }

        stage('Linting') {
            steps {
                script {
                    sh "pylint Dec2Hex.py || true" // Run pylint but do not fail the pipeline on warnings
                }
            }
        }

        stage('Unit Tests') {
            steps {
                script {
                    // If you have a test script, replace 'test_script.py' with actual test filename
                    sh "${PYTHON} -m unittest discover || true"
                }
            }
        }

        stage('Execution') {
            steps {
                script {
                    sh "${PYTHON} Dec2Hex.py 255" // Example input for testing
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline execution completed."
        }
        failure {
            echo "Build failed! Check logs for more details."
        }
    }
}
