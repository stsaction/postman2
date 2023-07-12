pipeline {
    agent any

    stages {
        stage('Checkout code') {
            steps {
                checkout scm
            }
        }

        stage('Install Node.js and npm') {
            steps {
                tool 'NodeJS14'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install mocha chai'
            }
        }

        stage('Install Postman SDK') {
            steps {
                sh 'npm install --global postman-collection@latest postman-runtime@latest'
            }
        }

        stage('Install Chai') {
            steps {
                sh 'npm install --save-dev chai'
            }
        }

        stage('Run Postman tests - Create') {
            steps {
                sh 'mocha create-test-scripts.js --reporter spec'
                catchError { error -> currentBuild.result = 'FAILURE' }
            }
        }

        stage('Run Postman tests - Delete') {
            steps {
                sh 'mocha delete-test-scripts.js --reporter spec'
                catchError { error -> currentBuild.result = 'FAILURE' }
            }
        }

        stage('Run Postman tests - Get') {
            steps {
                sh 'mocha get-test-scripts.js --reporter spec'
                catchError { error -> currentBuild.result = 'FAILURE' }
            }
        }

        stage('Run Postman tests - Update') {
            steps {
                sh 'mocha update-test-scripts.js --reporter spec'
                catchError { error -> currentBuild.result = 'FAILURE' }
            }
        }
    }
}
