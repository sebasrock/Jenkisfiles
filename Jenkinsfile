pipeline {
  agent any
  triggers {
    cron('H */4 * * 1-5')
  }
  options {
    buildDiscarder(logRotator(numToKeepStr:'50'))
  }

 stages {
        stage('Set Parammeter') {

          steps {
                echo 'Building..'

                echo "User: ${username} said Ok."
          }
        }
 }
}
