pipeline {
    stages {
        stage('Hello world') {
            steps {
                echo 'Hello world'
            }
        }
        node {
            checkout scm
        }
        stage('Build and Test .NET') {
            agent {
                docker { image 'mcr.microsoft.com/dotnet/core/sdk:3.1' }
            }
            environment {
                DOTNET_CLI_HOME = "/tmp/DOTNET_CLI_HOME"
            }
            stages {
                stage('Build .NET') {
                    dotnet build
                }
                stage('Test .NET') {
                    dotnet test
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Build TypeScript') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Test TypeScript') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Run Lint') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
