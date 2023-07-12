pipeline {
    agent any
    
    environment {
        NVM_DIR = '/var/lib/jenkins/.nvm'
        NODE_VERSION = '14.17.0'
    }
    
    stages {
        stage('Prerequisites') {
            steps {
                script {
                    // Install NVM
                    sh 'curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash'

                    // Load NVM into the current shell
                    sh '[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"'

                    // Install Node.js using NVM
                    sh "nvm install ${NODE_VERSION}"

                    // Use the installed Node.js version
                    sh "nvm use ${NODE_VERSION}"

                    // Install necessary dependencies using npm
                    sh 'npm install chai mocha newman'
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
