import groovy.json.JsonSlurperClassic

@NonCPS
def parseJsonToMap(String json) {
    final slurper = new JsonSlurperClassic()
    return new HashMap<>(slurper.parseText(json))
}

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
        stage('ReadJson'){
          steps {
            script {
                def json = "{\n" +
                                    "  \"foo\":\"f00\",\n" +
                                    "  \"bar\":\"baa\"\n" +
                                    "}"

                echo "Parsing JSON: ${json}"

                def map1 = parseJsonToMap(json)

                echo  "foo = ${map1.foo}"
                echo  "bar = ${map1.bar}"
            }
          }
        }
        stage('ReadJson and Call MavenTest Job') {
          steps {
            script {
               def json = "{\n" +
                                "  \"foo\":\"f00\",\n" +
                                "  \"bar\":\"baa\"\n" +
                            "}"

                echo "Parsing JSON: ${json}"

                def map = parseJsonToMap(json)
            }
            build job: 'MavenTest',  parameters: [ string(name: 'userdb', defaultValue: 'Ricardo Jenkins') ]
          }
        }
      }
    }

  }
  environment{
    ChromeDriverPath = 'D:\\Testes a criar\\mavenProjectFinalExample\\chromedriver.exe'
    UserNameBD = 'agora'
    PasswordBD = 'password'
    JsonPath = 'D:\\Testes a criar\\test2.json'
  }
}
