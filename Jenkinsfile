// Jenkins CI/CD Lab - Final Integration Test v1.1

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
                // This line creates the XML file Jenkins needs to show the "Test Result" page
                bat 'echo ^<testsuite tests="1" failures="0"^>^<testcase classname="Lab8" name="SimulatedTest"/^>^</testsuite^> > test-results.xml'
            }
            post {
                always {
                    // This command tells Jenkins to parse the XML file we just created
                    junit 'test-results.xml'
                    echo 'Test stage complete.' 
                }
            }
        }

        stage('Archive') {
            steps {
                echo 'Archiving build artifacts...'
                // Updated to archive the XML so you can see it in the build summary
                archiveArtifacts artifacts: 'test-results.xml', allowEmptyArchive: true
            }
        }

        stage('Deploy') {
            steps {
                echo 'Simulating deployment...'
                bat 'if not exist "C:\\tmp\\deployed-app" mkdir "C:\\tmp\\deployed-app"'
                bat 'echo File content > index.html' 
                bat 'copy index.html "C:\\tmp\\deployed-app\\index.html"'
                echo 'Application deployed to C:/tmp/deployed-app'
            }
        }
    } 

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