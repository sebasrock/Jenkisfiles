pipeline {
  agent any
  triggers {
    cron('H */4 * * 1-5')
  }
  options {
    buildDiscarder(logRotator(numToKeepStr:'50'))
  }

  environment {
		OUTPUT_PATH = './outputs/'
	}

 stages {
        stage('Set Parammeter') {

          input{
	          	message "Press Ok to continue"
	          	submitter "user1,user2"
		        parameters {
			        string(name:'username', defaultValue: 'user', description: 'Username of the user pressing Ok')
		        }
	      }

          steps {
                echo 'Building..'

                echo "User: ${username} said Ok."
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


}
