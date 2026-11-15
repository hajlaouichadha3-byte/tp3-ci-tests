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
                    dotnet restore dotnet-app/ProjectFile.csproj
                    dotnet restore dotnet-app.Tests/ProjectFile-Tests.csproj
                    dotnet test dotnet-app.Tests/ProjectFile-Tests.csproj
                '''
            }
        }

        stage('Test Python') {
            steps {
                echo 'Tests Python...'
                bat '''
                    cd python-app
                    python -m unittest
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Tous les tests ont réussi.'
        }
        failure {
            echo '❌ Un ou plusieurs tests ont échoué.'
        }
    }
}
