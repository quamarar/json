pipeline {
  agent any


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
                  jsonfile['environment'] = 'Arfa'
                  writeJSON file: 'job.json', json: jsonfile
           }
         }
       }
     }  
}
