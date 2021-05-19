pipeline {
    agent any

    stages {
        stage('Frontend') {
            agent {docker{image "node:14-alpine"}}
            steps {
                dir("DotnetTemplate.Web/") {
                    sh "npm install"
                    sh "npm run built"
                    sh "npm run lint"
                    sh "npm run tests"
                }

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
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}