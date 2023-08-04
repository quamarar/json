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
                  jsonfile =readJSON file: 'input.json', returnPojo: true
                  jsonfile['environment'] = 'Arfa'
                  writeJSON file: 'input.json', json: jsonfile
           }
         }
       }
     }  
}
