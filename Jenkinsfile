pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                checkout scm
            }
        }

        stage('Run Python Script') {
            steps {
                script {
                    // Define the decimal value to convert (you can change this value as needed)
                    def decimalValue = 255

                    // Execute the Python script with the decimal value as an argument
                    sh "python3 Dec2Hex.py ${decimalValue}"
                }
            }
        }
    }

    post {
        always {
            // Clean up or additional actions can be added here
            echo 'Pipeline execution completed.'
        }
    }
}
