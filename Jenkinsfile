pipeline {
  agent any

  parameters {
    string(defaultValue: "abc", description: 'Environment', name: 'ENV')

 stages {
       stage('checkout') {
         steps {
           git 'https://github.com/quamarar/json.git'
         }
        }
        stage('Adding Parameter') {
         steps {
           script {
                  jsonfile =readJSON file: 'job.json', returnPojo: true
                  jsonfile['environment'] = ${ENV}
                  writeJSON file: 'job.json', json: jsonfile
           }
         }
       }
     }  
}
