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

        stage('Install Newman') {
            steps {
                script {
                    // Change to the project directory
                    dir('/var/lib/jenkins/projects/Sample') {
                        // Install Newman globally
                        sh 'npm install -g newman'
                    }
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Define the paths to the test files, collections, and environment
                    def testFilesPath = '/var/lib/jenkins/projects/Sample/create-test-scripts.js'
                    def collectionFile = '/var/lib/jenkins/projects/Sample/Sample_APIs.postman_collection.json'
                    def environmentFile = '/var/lib/jenkins/projects/Sample/Sample_environment.postman_environment.json'

                    // Run the test files using Newman
                    sh "newman run ${collectionFile} --environment ${environmentFile}"
                }
            }
        }
    }
}
