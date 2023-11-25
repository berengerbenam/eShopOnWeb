pipeline {
  agent any
  stages {
    stage('Build1') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet build eshoponweb.sln'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test tests/IntegrationTests'
          }
        }

        stage('Functional') {
          steps {
            sh 'dotnet test tests/FunctionalTests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh 'dotnet publish eshoponweb.sln -o /var/aspnet'
      }
    }

  }
}