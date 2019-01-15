pipeline {
  agent any
  stages {
    stage('Set Parammeter') {
      parallel {
        stage('Set Parammeter') {
          steps {
            echo 'Building..'
            echo "User: ${username} said Ok."
          }
        }
        stage('test') {
          steps {
            sh 'echo "bitxh"'
          }
        }
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