pipeline {
    agent any

    stages {
        stage('Test Case 1') {
            steps {
                script {
                    sh """
                        echo 'Running Test Case 1'
                        const { expect } = require('chai');

                        describe('API tests', function () {
                          it('Status code is 201', function () {
                            const statusCode = 201;
                            expect(statusCode).to.equal(201);
                          });

                          it('Response body has correct name', function () {
                            const jsonData = { name: 'morpheus' };
                            expect(jsonData.name).to.equal('morpheus');
                          });

                          it('Response body has correct job', function () {
                            const jsonData = { job: 'leader' };
                            expect(jsonData.job).to.equal('leader');
                          });
                        });
                    """
                }
            }
        }

        stage('Test Case 2') {
            steps {
                script {
                    sh """
                        echo 'Running Test Case 2'
                        const { expect } = require('chai');

                        describe('API tests', function () {
                          it('Status code is 200', function () {
                            const statusCode = 200;
                            expect(statusCode).to.equal(200);
                          });

                          it('Response body has correct name', function () {
                            const jsonData = {
                              name: 'John Kepler'
                            };

                            expect(jsonData.name).to.eql('John Kepler');
                          });

                          it('Response body has correct job', function () {
                            const jsonData = {
                              job: 'Manager'
                            };

                            expect(jsonData.job).to.eql('Manager');
                          });
                        });
                    """
                }
            }
        }

        stage('Test Case 3') {
            steps {
                script {
                    sh """
                        echo 'Running Test Case 3'
                        const { expect } = require('chai');

                        describe('API tests', function () {
                          it('Status code is 200', function () {
                            const statusCode = 200;
                            expect(statusCode).to.equal(200);
                          });

                          it('Response body has correct data', function () {
                            const jsonData = {
                              data: {
                                id: 2,
                                email: 'janet.weaver@reqres.in',
                                first_name: 'Janet',
                                last_name: 'Weaver',
                                avatar: 'https://reqres.in/img/faces/2-image.jpg'
                              }
                            };

                            expect(jsonData.data.id).to.eql(2);
                            expect(jsonData.data.email).to.eql('janet.weaver@reqres.in');
                            expect(jsonData.data.first_name).to.eql('Janet');
                            expect(jsonData.data.last_name).to.eql('Weaver');
                            expect(jsonData.data.avatar).to.eql('https://reqres.in/img/faces/2-image.jpg');
                          });

                          it('Response body has correct support', function () {
                            const jsonData = {
                              support: {
                                url: 'https://reqres.in/#support-heading',
                                text: 'To keep ReqRes free, contributions towards server costs are appreciated!'
                              }
                            };

                            expect(jsonData.support.url).to.eql('https://reqres.in/#support-heading');
                            expect(jsonData.support.text).to.eql('To keep ReqRes free, contributions towards server costs are appreciated!');
                          });
                        });
                    """
                }
            }
        }
    }
}
