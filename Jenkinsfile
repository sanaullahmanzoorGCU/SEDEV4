pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/sanaullahmanzoorGCU/SEDEV4.git' // Replace with your actual repo URL
            }
        }
        
        stage('Setup Python Environment') {
            steps {
                script {
                    sh 'python3 -m venv venv' // Create virtual environment
                    sh 'source venv/bin/activate' // Activate virtual environment
                    sh 'pip install --upgrade pip' // Upgrade pip
                    sh 'pip install -r requirements.txt || echo "No requirements file found."' // Install dependencies if available
                }
            }
        }
        
        stage('Run Script') {
            steps {
                script {
                    sh 'python3 Dec2Hex.py 255' // Example execution
                }
            }
        }
    }
}
