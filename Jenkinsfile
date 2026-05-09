// Jenkins CI/CD Lab - Final Integration Test v1.0

pipeline {
    agent any

    environment {
        APP_NAME = 'your-app-name'
        BUILD_DIR = 'target' 
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                bat 'echo Build step — replace with your command'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'echo Test step — replace with your command'
            }
            post {
                always {
                    echo 'Test stage complete.' 
                }
            }
        }

        stage('Archive') {
            steps {
                echo 'Archiving build artifacts...'
                archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
            }
        }

        stage('Deploy') {
            steps {
                echo 'Simulating deployment...'
                // Fixed: Moved inside the stages block and cleaned up syntax
                bat 'if not exist "C:\\tmp\\deployed-app" mkdir "C:\\tmp\\deployed-app"'
                bat 'echo File content > index.html' // Ensuring file exists for the copy command
                bat 'copy index.html "C:\\tmp\\deployed-app\\index.html"'
                echo 'Application deployed to C:/tmp/deployed-app'
            }
        }
    } // This bracket correctly closes the STAGES section

    post {
        success {
            echo "SUCCESS: Email notification would be sent to your email."
            echo "Build #${env.BUILD_NUMBER} completed successfully."
        }
        failure {
            echo "FAILURE: Alerting developer."
            echo "Build #${env.BUILD_NUMBER} has failed. Check the logs."
        }
    }
}