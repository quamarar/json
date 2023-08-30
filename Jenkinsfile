


pipeline {
  agent any

environment {
      s3_bucket_name_internal = "msil-poc-apsouth1-internal"
      s3_bucket_name_shared = "msil-poc-apsouth1-shared"
     
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
                    def amap = ['athena_pred_or_eval_table_name': 'evaluation','athenadb_name': 'default','athenadb_debug_table_name': 'debug',
                                'athenadb_evaluation_summary_table_name': 'model_eval_summary','train_statetable_name': 'template-dapm-dev-apsouth1-state-table',
                                'train_inputtable_name': 'template-dapm-dev-apsouth1-input-table','train_metatable_name': 'template-dapm-dev-apsouth1-meta-table',
                                's3_bucket_name_internal': 'template-dapm-dev-apsouth1-internal','s3_bucket_name_shared': 'template-dapm-dev-apsouth1-shared',
                                'mapping_json_S3_path': 's3://template-dapm-dev-apsouth1-internal/mapping_json/mapping_json.json','region': 'ap-south-1',
                                 'use_case_name': 'DCP', 'aws_batch_job_queue': 'arn:aws:batch:ap-south-1:731580992380:job-queue/template-dapm-dev-apsouth1-dapf-batch-training-job-queue',
                                'aws_batch_job_name': 'aws_demo_batch_run','athenadb_metadata_table_name': 'meta','ssm_training_complete_status': '/template-dapm-dev-apsouth1/training_complete_status',
                                'dq_athena_db': 'poc_monitoring','dq_table': 'dqresults','email_topic_arn': 'arn:aws:sns:ap-south-1:731580992380:model_start_dq_notification',
                                'training_event_bus_name': 'async_monitoring_event_bus','repository': 'github/maruti-modelops/quality-mlops-defect-corelation-and-prediction.git']
                                 
                   writeJSON file: 'data.json', json: amap
                   def read = readJSON file: 'data.json'

                   assert read.year == "${Year}"
                   assert read.athena_pred_or_eval_table_name == 'evaluation'
                   assert read.athenadb_name == 'default'
                   assert read.athenadb_debug_table_name == 'debug'
                   assert read.athenadb_evaluation_summary_table_name == 'model_eval_summary'
                   assert read.train_statetable_name == 'template-dapm-dev-apsouth1-state-table'
                   assert read.train_inputtable_name == 'template-dapm-dev-apsouth1-input-table'
                   assert read.train_metatable_name == 'template-dapm-dev-apsouth1-meta-table'
                   assert read.s3_bucket_name_internal == 'template-dapm-dev-apsouth1-internal'
                   assert read.s3_bucket_name_shared == 'template-dapm-dev-apsouth1-shared'
                   assert read.mapping_json_S3_path == 's3://template-dapm-dev-apsouth1-internal/mapping_json/mapping_json.json'
                   assert read.region == 'ap-south-1'
                   assert read.use_case_name == 'DCP'
                   assert read.aws_batch_job_queue == 'arn:aws:batch:ap-south-1:731580992380:job-queue/template-dapm-dev-apsouth1-dapf-batch-training-job-queue'
                   assert read.aws_batch_job_name == 'aws_demo_batch_run'
                   assert read.athenadb_metadata_table_name == 'meta'
                   assert read.ssm_training_complete_status == '/template-dapm-dev-apsouth1/training_complete_status'
                   assert read.dq_athena_db == 'poc_monitoring'
                   assert read.dq_table == 'dqresults'
                   assert read.email_topic_arn == 'arn:aws:sns:ap-south-1:731580992380:model_start_dq_notification'
                   assert read.training_event_bus_name == 'async_monitoring_event_bus'
                   assert read.repository == 'github/maruti-modelops/quality-mlops-defect-corelation-and-prediction.git'
             

           }     
         }
       }
 }
}
  
   
