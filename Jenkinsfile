pipeline {
agent any
parameters {
  string(name: 'user', defaultValue: 'John', description: 'A user that triggers the pipeline')
  booleanParam(defaultValue: true, description: '', name: 'userFlag')
  choice(
        name: 'myParameter',
        choices: "Option1\nOption2",
        description: 'interesting stuff' )
}
stages {
stage('Trigger pipeline') {
steps {
   echo "Pipeline triggered by ${params.user}"
   echo "flag: ${params.userFlag}"
   echo "flag: ${params.myParameter}"
}
}
}
}
