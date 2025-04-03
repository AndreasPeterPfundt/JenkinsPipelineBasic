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
            echo "Get the DriverPath ${ChromeDriverPath}"
          }
        }

        stage('Test Log') {
          steps {
            writeFile(file: 'LogTestFile.txt', text: 'This is an automation file log')
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            input(message: 'Do you want to Diploy?', id: 'OK')
            echo 'Deploung the app is IIS server'
          }
        }

        stage('Artifacts') {
          steps {
            archiveArtifacts 'LogTestFile.txt'
          }
        }

      }
    }

  }
  environment {
    ChromeDriverPath = 'C:\\ProgramData\\chocolatey\\lib\\chromedriver'
  }
}