pipeline {
  agent any
  stages {
    stage('Launch Deploy/Dump') {
      parallel {
        stage('Launch Deploy/Dump') {
          steps {
            echo 'Launching Dump/Deploy on ServerTest'
          }
        }

        stage('Launch Test') {
          steps {
            echo 'Launching Test Get Tarif on Server Test'
          }
        }

      }
    }

    stage('Launch Deploy/Dump 2') {
      parallel {
        stage('Launch Deploy/Dump 2') {
          steps {
            echo 'Launch another Deploy and Dump on other Server for tests'
          }
        }

        stage('Launch Test 2') {
          steps {
            echo 'Launching Test Login on Server Test 2'
          }
        }

      }
    }

  }
}