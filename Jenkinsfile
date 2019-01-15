pipeline {
  agent any
 
  stages {
		stage ('build') {			
  
	    steps {
        input{
		      message "Press Ok to continue"
		      submitter "user1,user2"
		      parameters {
			      string(name:'username', defaultValue: 'user', description: 'Username of the user pressing Ok')
		      }
	      } 
		  echo "User: ${username} said Ok."
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
