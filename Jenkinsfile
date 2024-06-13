pipeline {
    agent any

    environment {
        DOTNET_VERSION = '8.0'
        BUILD_CONFIGURATION = 'Release'
    }

    stages {
        stage('Checkout') {
            steps {
                // Étape pour récupérer le code source à partir du référentiel Git
                git 'https://github.com/pro861/apptest0.test.git'
            }
        }

        stage('Build') {
            steps {
                // Étape pour restaurer les dépendances, compiler le projet et générer les artefacts de build
                script {
                    sh "dotnet restore apptest0/apptest0.csproj"
                    sh "dotnet build apptest0/apptest0.csproj -c ${BUILD_CONFIGURATION} -o /app/build"
                }
            }
        }

        stage('Test') {
            steps {
                // Étape pour exécuter les tests unitaires ou d'intégration de l'application .NET
                script {
                    sh "dotnet test apptest0/apptest0.csproj --configuration ${BUILD_CONFIGURATION}"
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
