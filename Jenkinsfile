pipeline {
    agent any
    tools {
        nodejs 'NodeJS' // Name of your Node.js installation in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                git url: 'https://github.com/your-repo/your-project.git',
                    branch: 'main'
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install Node.js dependencies
                sh 'npm install'
            }
        }
        stage('Build with Maven') {
            steps {
                // Build the application using Maven
                sh 'mvn clean package'
            }
        }
        stage('Run Selenium Tests') {
            steps {
                // Run Selenium tests
                sh 'mvn test -Dtest=YourSeleniumTestClass'
            }
        }
    }
    post {
        success {
            echo 'Build and tests were successful!'
        }
        failure {
            echo 'Build or tests failed!'
        }
        always {
            echo 'Cleaning up...'
        }
    }
}
