
pipeline {
    agent any
     //triggers {
       // cron('H */4 * * 1-5')
   // }
    options {
       // ansiColor('xterm')
        // timeout(time: 6, unit: 'HOURS')
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
        

        // Mule parameters
        string(name: 'MULE_BUILD', defaultValue: 'DEFAULT',
                description: '''mule-enterprise-standalone-4.2.0-SNAPSHOT
                                mule-enterprise-standalone-4.1.4
                                mule-enterprise-standalone-4.1.5
                                mule-enterprise-standalone-4.1.6-SNAPSHOT''')
        booleanParam(name: 'FLOWSTACK_ENABLED', defaultValue: false, description: '')
        choice(name: 'JDK', choices: ['one', 'two', 'three'], description: '')
        choice(name: 'GC', choices: ['one', 'two', 'three'], description: '')  
    
    }
    stages {
         stage('download to the runtime') {
             steps {
                // Git checkout before load source the file
                echo "Pipeline triggered by ${params.MULE_BUILD}"
               
                //def props = readProperties interpolate: true, file: 'test.properties''

                 script {
                    downloadRuntumeVersion()
                }
            }
         }
        stage('SetUp the runtime') {
             steps {
                script {
                    setUpRuntumeVersion()
                }

            }
            
         }
           stage('start the runtime') {
             steps {
                script {
                    startRuntime()
                }

            }
            
         }
            stage('downdload the app') {
             steps {
                script {
                    downloadApp()
                }

            }
            
         }

    }
}

def downloadRuntumeVersion() {
    
   //Conected for ssh to the server 
   echo "Download mule runtime version ===> ${params.MULE_BUILD}"
   //TODO it's necesary add credential with private nexus
    //sh "wget  https://repository.mulesoft.org/nexus/content/repositories/releases/org/mule/distributions/mule-standalone/3.5.0/mule-standalone-3.5.0.tar.gz"
    sh " curl -u perf.test:h_-3LpBfW2UZUwPd https://repository.mulesoft.org/nexus/content/groups/private/com/mulesoft/mule/distributions/mule-ee-distribution-standalone/4.2.0-SNAPSHOT/mule-ee-distribution-standalone-4.2.0-20190124.201409-3098.tar.gz -O -J -L"
    sh "tar xvzf ${pwd()}/mule-ee-distribution-standalone-4.2.0-20190124.201409-3098.tar.gz"

    //dowload page withe number of rumtime and just dowload the last

}

def setUpRuntumeVersion() {
    
   //Conected for ssh to the server 
   echo "SetUp mule runtime version ===> ${params.MULE_BUILD}"
   //TODO it's necesary add credential with private nexus
   //sh "cd /mule-standalone-3.5.0/conf"

   echo " ===> ${pwd()}"
  
   def readContent = readFile './mule-enterprise-standalone-4.2.0-SNAPSHOT/conf/wrapper.conf'

   writeFile file: './mule-enterprise-standalone-4.2.0-SNAPSHOT/conf/wrapper.conf', text: readContent+"\r\r\r\n############### ADD BY JOB #########################"

//TODO get consecutive number from the conte file

   if (params.FLOWSTACK_ENABLED) {
    readContent = readFile './mule-enterprise-standalone-4.2.0-SNAPSHOT/conf/wrapper.conf'
     writeFile file: './mule-enterprise-standalone-4.2.0-SNAPSHOT/conf/wrapper.conf', text: readContent+"\r\nwrapper.java.additional.99=-Dmule.flowTrace=TRUE"
   }
}

def startRuntime() {
   
    
   //Conected for ssh to the server 
    echo "startRuntime mule runtime version ===> ${params.MULE_BUILD}"
   
    sh "sh ./mule-enterprise-standalone-4.2.0-SNAPSHOT/bin/mule  > startRun.log"

    sleep 30s

    def existLogMuleEE = fileExists './mule-enterprise-standalone-4.2.0-SNAPSHOT/logs/mule_ee.log'


}

def downloadApp() {
    
   //Conected for ssh to the server 
   //git fetch 
   //git pull
   //SCP app
    //git archive --format tar --remote ssh://server.org/path/to/git HEAD docs/usage > /tmp/usage_docs.tgz
    sh "cp -avr /Users/ssanchezc/Documents/mule/repository/performanceworks/APPS/Mule4/4.2.0-SNAPSHOT/FLOW-STACK/http-proxy-flowref ./mule-enterprise-standalone-4.2.0-SNAPSHOT/apps/"

    sleep 30

    def existLogMuleEE = fileExists './mule-enterprise-standalone-4.2.0-SNAPSHOT/logs/mule_ee.log'
}
