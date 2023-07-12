pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    // Create a directory to store the locally installed packages
                    dir('node_modules') {
                        // Install necessary dependencies using npm locally
                        sh 'npm install chai mocha newman @babel/register'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Define the path to the test files, collections, and environments
                    def testFilesPath = 'create-test-scripts'
                    def collectionFile = 'Sample_APIs.postman_collection.json'
                    def environmentFile = 'Sample_environment.postman_environment.json'

                    // Run the test files using Mocha and Newman with @babel/register
                    sh "npx mocha --require @babel/register ${testFilesPath}.js"
                    sh "npx newman run ${collectionFile} --environment ${environmentFile}"
                }
            }
        }
    }
}
