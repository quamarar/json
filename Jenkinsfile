pipeline {
  agent any

  parameters {
        string(name: 'execution_month', defaultValue: 'August', description: 'Month of excecution')
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
                  writeJSON file: 'input.json', json: jsonfile
           }
         }
       }
     }  
}
