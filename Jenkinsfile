pipeline {
  agent any
  stages {
    stage('Buikd') {
      parallel {
        stage('Buikd') {
          steps {
            echo 'Building the .NET Core application'
          }
        }

        stage('Test') {
          steps {
            echo 'Testing the application'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploung the app is IIS server'
      }
    }

  }
}