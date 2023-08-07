


pipeline {
  agent any

environment {
      s3_bucket_name_internal = "msil-poc-apsouth1-internal"
      s3_bucket_name_shared = "msil-poc-apsouth1-shared"
      excecution_time = "${BUILD_TIMESTAMP}"
     
  }


  
 stages {
       stage('checkout') {
         steps {
           git 'https://github.com/quamarar/json.git'
         }
        }
    

        stage('Adding Parameter') {
         steps {
           script {
                  jsonfile =readJSON file: 'input.json', returnPojo: true
                  jsonfile['s3_bucket_name_internal'] = "${s3_bucket_name_internal}"
                  jsonfile['s3_bucket_name_shared'] = "${s3_bucket_name_shared}"
                  jsonfile['excecution_Timetstamp'] = "${BUILD_TIMESTAMP}"
                  writeJSON file: 'input.json', json: jsonfile
           }
               def result = sh 'echo $(excecution_time)| awk '{print $1}'' 
               
         }
       }
      stage('Invoking step function'){
        steps{
          withAWS(roleAccount:'731580992380', role:'Cross-Account-role') {
         sh 'aws stepfunctions start-execution --state-machine-arn arn:aws:states:ap-south-1:731580992380:stateMachine:MSILStateMachine --input "$(jq -R . input.json --raw-output)" --region ap-south-1'
     }  
  }
 }
}
}
   
