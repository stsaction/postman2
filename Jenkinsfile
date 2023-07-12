pipeline {
    agent any

    stages {
         stage('Prepare Environment') {
            steps {
                script {
                    // Create a directory for the project and give permissions to Jenkins user
                    sh 'mkdir -p /var/lib/jenkins/projects/Sample'
                    sh 'chown -R jenkins:jenkins /var/lib/jenkins/projects/Sample'
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                    dir('/var/lib/jenkins/projects/Sample') {
                        // Install necessary dependencies using npm locally
                        sh 'npm init -y'
                        sh 'npm install --no-save chai mocha newman esm'
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
                    sh "npx mocha --require esm ${testFilesPath}.js"
                    sh "npx newman run ${collectionFile} --environment ${environmentFile}"
                }
            }
        }
    }
}
