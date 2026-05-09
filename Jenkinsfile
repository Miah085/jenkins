pipeline {
    agent any

    environment {
        APP_NAME = 'your-app-name'
        BUILD_DIR = 'target'   // or 'build', 'dist' for your project
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
                // Maven:  sh 'mvn clean package -DskipTests'
                // Gradle: sh './gradlew build'
                // npm:    sh 'npm install && npm run build'
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
                    // We add an echo here so the block isn't empty
                    echo 'Test stage complete.' 
                    // junit '**/target/surefire-reports/*.xml'
                }
            }
        }

        stage('Archive') {
            steps {
                echo 'Archiving build artifacts...'
                archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
            }
        }
    }

    stage('Deploy') {
            steps {
                echo 'Simulating deployment...'
                // Creates the directory if it doesn't exist
                bat 'if not exist "C:\\tmp\\deployed-app" mkdir "C:\\tmp\\deployed-app"'
                // Copies your project files to the deployment folder
                bat 'copy index.html "C:\\tmp\\deployed-app\\index.html"'
                echo 'Application deployed to C:/tmp/deployed-app'
            }
        }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline FAILED — check the logs above.'
        }
    }
}
