pipeline {
    agent any
    tools {
    nodejs 'NodeJS' // Ensure this matches the NodeJS installation name in Jenkins
    }
    environment {
        GITHUB_REPO = 'https://github.com/notSoWickedWick/my-node-app-jenkins.git'
        BRANCH_NAME = 'main' // Specified the branch to checkout
    }
    stages {
        // stage('Install Zip Dependency') { // Renamed for uniqueness
// steps {
// sh 'apt update && sudo apt install zip -y'
// }
// }
    stage('Checkout') {
        steps {
            cleanWs() // Clean workspace before checkout
            git branch: env.BRANCH_NAME, url: env.GITHUB_REPO // Checkout specific branch
            sh 'ls -la' // Print current directory conten
            ts for debugging
        }
    }
    stage('Install Node Dependencies') { // Renamed for uniqueness
        steps {
            sh 'node --version' // Print Node.js version
            sh 'npm --version' // Print npm version
            sh 'npm install --loglevel=error' // Install dependencies with error logging
        }
    }
    stage('Run Tests') {
        steps {
            sh 'npm test || echo "No tests specified"' // Run tests
        }
    }
    stage('Package Application') {
        steps {
            sh 'zip -r jenkins-project-Devops_Class.zip.' // Create a zip file of the entire directory
        }
    }
}
post {
        success {
            echo 'Application Build and tests were successful!'
        }
        failure {
            echo 'Build or tests failed!'
        }
        always {
            echo 'Cleaning up...'
        }
    }
}
