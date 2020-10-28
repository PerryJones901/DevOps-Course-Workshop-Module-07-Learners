pipeline {
    agent any
    stages {
        stage('Build and Test .NET') {
            agent {
                docker { image 'mcr.microsoft.com/dotnet/core/sdk:3.1' }
            }
            environment {
                DOTNET_CLI_HOME = "/tmp/DOTNET_CLI_HOME"
            }
            stages {
                stage('Build .NET') {
                    steps {
                        sh 'dotnet build'
                    }
                }

                stage('Test .NET') {
                    steps {
                        sh 'dotnet test'
                    }
                }
            }
        }

        stage('npm Stuff') {
            agent {
                docker { image 'node:14-alpine' }
            }

            stages {
                stage('Install Dependencies') {
                    steps {
                        dir('DotnetTemplate.Web') {
                            sh 'npm install'
                        }
                    }
                }

                stage('Build TypeScript') {
                    steps {
                        dir('DotnetTemplate.Web') {
                            sh 'npm run build'
                        }
                    }
                }

                stage('Test TypeScript') {
                    steps {
                        dir('DotnetTemplate.Web') {
                            sh 'npm t'
                        }
                    }
                }

                stage('Run Lint') {
                    steps {
                        dir('DotnetTemplate.Web') {
                            sh 'npm run lint'
                        }
                    }
                }
            }
        }
    }
}
