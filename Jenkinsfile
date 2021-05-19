pipeline {
    agent any
    environment {
        DOTNET_CLI_HOME = "/tmp/DOTNET_CLI_HOME"
    }

    stages {
        stage('Frontend') {
            agent {docker{image "node:14-alpine"}}
            steps {
                dir("DotnetTemplate.Web/") {
                    sh "npm install"
                    sh "npm run build"
                    sh "npm run lint"
                    sh "npm run test"
                }
            }
        }
        stage('Testing backend') {
            agent {docker{image 'mcr.microsoft.com/dotnet/skd:5.0"'}}
            steps {
                sh "dotnet build"
                sh "dotnet test"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}