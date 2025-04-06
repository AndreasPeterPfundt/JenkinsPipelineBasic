pipeline {
  agent any
  stages {
    stage('Build') {
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
          environment {
            LocalVariable = 'HelloLocal'
          }
          steps {
            writeFile(file: 'LogTestFile.txt', text: "This is ${ChromeDriverPath} and localvariable Value ${LocalVariable}")
          }
        }

      }
    }

    stage('Deploy') {
  parallel {
    stage('Deploy') {
      when {
        branch 'master'
      }
      steps {
        input(message: 'Do you want to Deployment ?', id: 'OK')
        echo 'Deploying the app to IIS server'
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