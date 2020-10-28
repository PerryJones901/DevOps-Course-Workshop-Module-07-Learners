pipeline {
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
            dir('DotnetTemplate.Web') {
                stages {
                    stage('Install Dependencies') {
                        steps {
                            sh 'npm install'
                        }
                    }

                    stage('Build TypeScript') {
                        steps {
                            sh 'npm run build'
                        }
                    }

                    stage('Test TypeScript') {
                        steps {
                            sh 'npm t'
                        }
                    }

                    stage('Run Lint') {
                        steps {
                            sh 'npm run lint'
                        }
                    }
                }
            }
        }
    }
}
