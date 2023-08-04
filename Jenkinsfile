pipeline {
  agent any

  parameters {
        string(name: 'execution_month', defaultValue: 'August', description: 'Month of excecution')
        string(name: 's3_output_bucket_name_training', defaultValue: 'training_bucket', description: 'Name of training bucket')
        string(name: 's3_output_bucket_name_evaluation', defaultValue: 'evaluation_bucket', description: 'Name of evaluation bucket')
        string(name: 's3_output_bucket_name_lineage', defaultValue: 'lineage_bucket', description: 'Name of lineage bucket')
        string(name: 's3_output_bucket_name_statestore', defaultValue: 'statestore_bucket', description: 'Name of statestore bucket')
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
                  jsonfile['execution_month'] = "${execution_month}"
                  jsonfile['s3_output_bucket_name_training'] = "${s3_output_bucket_name_training}"
                  jsonfile['s3_output_bucket_name_evaluation'] = "${s3_output_bucket_name_evaluation}"
                  jsonfile['s3_output_bucket_name_lineage'] = "${s3_output_bucket_name_lineage}"
                  jsonfile['s3_output_bucket_name_statestore'] = "${s3_output_bucket_name_statestore}"
                  writeJSON file: 'input.json', json: jsonfile
           }
         }
       }
     }  
}
