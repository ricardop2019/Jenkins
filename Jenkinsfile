pipeline {
  agent any
  stages {
    stage('Launch Deploy/Dump') {
      parallel {
        stage('Launch Deploy/Dump') {
          steps {
            echo 'Launching Dump/Deploy on ServerTest'
            echo 'connecting to BD'
            echo "Username: ${UserNameBD}"
            echo "Password: ${PasswordBD}"
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

    stage('Calling others Jobs') {
      parallel {
        stage('Call job FreeJob1') {
          steps {
            build job: 'FreeJob1'
          }
        }
        stage ('ReadJson'){
          steps {
            def props = readJSON file: ${JsonPath}
          }
        }
        stage('Call MavenTest Job') {
          steps {
            build job: 'MavenTest'
          }
        }
      }
    }

  }
  environment{
    ChromeDriverPath = 'D:\\Testes a criar\\mavenProjectFinalExample\\chromedriver.exe'
    UserNameBD = 'agora'
    PasswordBD = 'password'
    JsonPath = 'D:\\Testes a criar\\test.json'
  }
}
