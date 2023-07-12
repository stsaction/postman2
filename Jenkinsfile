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
                        // Install Newman globally
                        sh 'apt-get update' 
                        sh 'npm install -y newman'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Define the paths to the collection and environment files
                    def collectionFile = '/var/lib/jenkins/projects/Sample/Sample_APIs.postman_collection.json'
                    def environmentFile = '/var/lib/jenkins/projects/Sample/Sample_environment.postman_environment.json'

                    // Read the test cases file
                    def testCasesFile = readFile('/var/lib/jenkins/projects/Sample/testCases.js')

                    // Generate a temporary test file with the test cases
                    def tempTestFile = writeFile file: '/var/lib/jenkins/projects/Sample/tempTestFile.js', text: testCasesFile

                    // Run the test file using Newman
                    sh "newman run ${collectionFile} --environment ${environmentFile} --delay-request 1000 --script ${tempTestFile}"
                }
            }
        }
    }
}
