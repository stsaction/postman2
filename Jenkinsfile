pipeline {
    agent any

    stages {
        stage('Prerequisites') {
            steps {
                script {
                    // Install necessary dependencies
                    sh 'npm install -g chai mocha newman'
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

                    // Run the test files using Mocha and Newman
                    sh "mocha ${testFilesPath}.js"
                    sh "newman run ${collectionFile} --environment ${environmentFile}"
                }
            }
        }
    }
}
