pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('Tests') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet test tests/UnitTest'
            sh 'dotnet test Tests/UnitTests'
          }
        }

        stage('Int�gration') {
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

    stage('deployment') {
      steps {
        sh 'dotnet publish eShopOnWeb-sln -o /var/aspnet'
      }
    }

  }
}