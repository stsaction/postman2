pipeline {
    agent any

    stages {
        stage('Prepare Environment') {
            steps {
                script {
                    sh 'mkdir -p /var/lib/jenkins/projects/Sample'
                    sh 'chown -R jenkins:jenkins /var/lib/jenkins/projects/Sample'
                }
            }
        }

        stage('Checkout code') {
            steps {
                checkout scm
            }
        }

        stage('Install Node.js and npm') {
            tools {
                nodejs 'node14'
            }
            steps {
                sh 'node --version'
                sh 'npm --version'
                sh 'npm install --global mocha@7.2.0 chai@4.3.4'
                sh 'npm install --global postman-collection@4.1.7 postman-runtime@7.32.3'
                sh 'npm install --save-dev chai@4.3.7'
                sh 'npx mocha create-test-scripts.js --reporter spec'
                sh 'npx mocha delete-test-scripts.js --reporter spec'
                sh 'npx mocha get-test-scripts.js --reporter spec'
            }
        }

        stage('Run Postman tests - Update') {
            steps {
                sh 'npx mocha update-test-scripts.js --reporter spec'
            }
        }
    }
}
