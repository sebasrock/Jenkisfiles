pipeline {
    agent any
     triggers {
        cron('H */4 * * 1-5')
    }
    options {
        timeout(time: 6, unit: 'HOURS')
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }
    parameters {
        // Client parameters
        string(name: 'THREADS', defaultValue: '10 20 60',
                description: '''e.g. 10 <br>
                                e.g. 10 20 40 80
                                e.g. 10 20 40 80 120 160
                                e.g. 10 40 80 120 160 200
                                e.g. 10 20 40 60 80 120 160
                                e.g. 10 20 40 60 80 100 120 140 160 180 200''')
        string(name: 'RAMPUP_TIME', defaultValue: '30')
        string(name: 'DURATION', defaultValue: '300')
        string(name: 'PAYLOAD_SIZES', defaultValue: '1KB 10KB 100KB',
                description: '''e.g. 1KB 10KB 100KB 500KB 1MB <br>''')
        

         // app parameters
        string(name: 'LOCATION_APP',description:' Localitation of app under path ...')
        string(name: 'PORT_APP',description:' Port to the application')
        string(name: 'BACKEND_PATH', defaultValue: '1KB.payload', description:'e.g. 10B.payload 1KB.payload 10KB.payload 100KB.payload 1MB.payload')
        string(name: 'BACKEND_DELAY_IN_MS', defaultValue: '70', description:'e.g. Default: 70 Adds a fixed delay in milliseconds to the VertX backend response')
        booleanParam(name: 'FLOWSTACK_ENABLED', defaultValue: false, description: '')
        choice(name: 'JDK', choices: ['one', 'two', 'three'], description: '')
        choice(name: 'GC', choices: ['one', 'two', 'three'], description: '')  

        // Mule parameters
        string(name: 'MULE_BUILD', defaultValue: 'DEFAULT',
                description: '''mule-enterprise-standalone-4.2.0-SNAPSHOT
                                mule-enterprise-standalone-4.1.4
                                mule-enterprise-standalone-4.1.5
                                mule-enterprise-standalone-4.1.6-SNAPSHOT''')
    
    }
    stages {
         stage('Checkout Librarys') {
            
              @Step(title='List files')
              echo "Pipeline triggered by ${params.LOCATION_APP}"

             @Step(title='Do something')
             aStep 'do something'
         }
    }
}
