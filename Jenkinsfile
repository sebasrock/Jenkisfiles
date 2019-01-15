pipeline {
  agent any
  stages {
    stage('Creation of Infrastructure') {
      steps {
        echo "User: ${username} said Ok."
      }
    }
    stage('Scripts Configuration') {
      steps {
        catchError()
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