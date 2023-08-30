


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
                    def amap = ['something': 'my datas',
                    'size': 3,
                    'isEmpty': false]
                     writeJSON file: 'data.json', json: amap
                    def read = readJSON file: 'data.json'

                   assert read.something == 'my datas'
                   assert read.size == 3
                   assert read.isEmpty == false

           }     
         }
       }
 }
}
  
   
