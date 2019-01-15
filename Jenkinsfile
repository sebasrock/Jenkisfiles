pipeline {
    agent any
     triggers {
        cron('H */4 * * 1-5')
    }
    options {
    // Only keep the 10 most recent builds
    buildDiscarder(logRotator(numToKeepStr:'10'))
  }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage(''Creation of Infrastructure') {
            failFast true
            parallel {
                stage('Creation of backend server') {
                    steps {
                        echo "On Branch A"
                    }
                }
                stage('Creation of client server) {
                    steps {
                        echo "On Branch B"
                    }
                    steps {
                        echo "On Branch B"
                    }
                }
                stage('Creation of procees server') {
                    stages {
                        stage('Nested 1') {
                            steps {
                                echo "In stage Nested 1 within Branch C"
                            }
                        }
                        stage('Nested 2') {
                            steps {
                                echo "In stage Nested 2 within Branch C"
                            }
                        }
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
     post {
        always {
             echo "Send notifications for result: ${currentBuild.result}"
    }
  }
}
