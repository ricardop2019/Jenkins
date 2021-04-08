pipeline {
  agent any
  stages {
    stage('Launch Deploy/Dump') {
      parallel {
        stage('Launch Deploy/Dump') {
          steps {
            echo 'Launching Dump/Deploy on ServerTest'
            echo 'connecting to BD'
            echo 'Username: ${UserNameBD}'
            echo 'Password: ${PasswordBD}'
          }
        }

        stage('Launch Test') {
          steps {
            echo 'Launching Test Get Tarif on Server Test'
            echo "Get the DriverPath ${ChromeDriverPath}"
          }
        }

      }
    }

    stage('Calling other Job') {
      parallel {
        stage('Call job FreeJob1') {
          steps {
            build job: 'FreeJob1'
          }
        }
      }
    }

  }
  environment{
    ChromeDriverPath = 'D:\\Testes a criar\\mavenProjectFinalExample\\chromedriver.exe'
    UserNameBD = 'agora'
    PasswordBD = 'password'
  }
}
