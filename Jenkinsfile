pipeline {
  agent any
  stages {
    stage('Creation of Infrastructure') {
      stages {
         stage('Creation of backend server') {
           steps {
            echo "User: said Ok."
          }
        }
        stage('Creation of client server') {
           steps {
            echo "User: said Ok."
          }
        }
         stage('Creation of procees server') {
           steps {
            echo "User: said Ok."
          }
        }
      }
    }
    stage('Scripts Configuration') {
      stages {
         stage('Creation of backend server') {
           steps {
            echo "User: said Ok."
          }
        }
        stage('Creation of client server') {
           steps {
            echo "User: said Ok."
          }
        }
      }
    }
    stage('Collector metrics') {
      steps {
       echo "User: said Ok."
      }
    }
  }
  options {
    buildDiscarder(logRotator(numToKeepStr: '50'))
  }
  triggers {
    cron('H */4 * * 1-5')
  }
}
