pipeline {
  agent any
 
  stages {
	
	}
  options {
    buildDiscarder(logRotator(numToKeepStr: '50'))
  }
  triggers {
    cron('H */4 * * 1-5')
  }
}
