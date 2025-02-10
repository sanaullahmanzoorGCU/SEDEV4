pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }
        
        stage('Setup') {
            steps {
                echo 'Setting up environment...'
                sh 'python3 -m venv venv'
                sh 'source venv/bin/activate && pip install --upgrade pip'
            }
        }
        
        stage('Lint') {
            steps {
                echo 'Running linter...'
                sh 'source venv/bin/activate && pip install flake8 && flake8 Dec2Hex.py'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'source venv/bin/activate && python3 -m unittest discover tests'
            }
        }
        
        stage('Run Script') {
            steps {
                echo 'Executing Dec2Hex.py with sample input...'
                sh 'source venv/bin/activate && python3 Dec2Hex.py 255'
            }
        }
        
        stage('Cleanup') {
            steps {
                echo 'Cleaning up environment...'
                sh 'rm -rf venv'
            }
        }
    }
}
