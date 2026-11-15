pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Récupération du code source...'
                checkout scm
            }
        }

        stage('Test .NET') {
            steps {
                echo 'Restauration et tests .NET...'
                bat '''
                    "C:\Program Files\dotnet\dotnet.exe" restore dotnet-app/ProjectFile.csproj
                    "C:\Program Files\dotnet\dotnet.exe" restore dotnet-app.Tests/ProjectFile-Tests.csproj
                    "C:\Program Files\dotnet\dotnet.exe" test dotnet-app.Tests/ProjectFile-Tests.csproj
                '''
            }
        }

        stage('Test Python') {
            steps {
                echo 'Tests Python...'
                bat '''
                    cd python-app
                    "C:\Users\DELL\AppData\Local\Programs\Python\Python311\python.exe" -m unittest
                '''
            }
        }
    }
}
