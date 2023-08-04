pipeline {
  agent any

environment {
      s3_output_bucket_name_training = "training_bucket"
      s3_output_bucket_name_evaluation = "evaluation_bucket"
      s3_output_bucket_name_lineage = "lineage_bucket"
      s3_output_bucket_name_statestore = "statestore_bucket"
  }

parameters {
  choice(name: 'Algo-list', choices:['LINEARREGRESSION', 'XGBOOST'], description:'Pick the Algo')
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
                  jsonfile['s3_output_bucket_name_training'] = "${s3_output_bucket_name_training}"
                  jsonfile['s3_output_bucket_name_evaluation'] = "${s3_output_bucket_name_evaluation}"
                  jsonfile['s3_output_bucket_name_lineage'] = "${s3_output_bucket_name_lineage}"
                  jsonfile['s3_output_bucket_name_statestore'] = "${s3_output_bucket_name_statestore}"
                  jsonfile['excecution_Timetstamp'] = "${BUILD_TIMESTAMP}"
                  jsonfile['Algo-list'] = "${Algo-list}"
                  writeJSON file: 'input.json', json: jsonfile
           }
         }
       }
      stage('Invoking step function'){
        steps{
         sh 'aws stepfunctions start-execution --state-machine-arn arn:aws:states:us-east-1:836350033173:stateMachine:BatchJobNotificationStateMachine-lPdtYhDEHlG0  --input "$(jq -R . input.json --raw-output)" --region us-east-1'
     }  
  }
 }
}
   
   
