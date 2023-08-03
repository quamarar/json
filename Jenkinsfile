pipeline {
  agent any

 stages {
       stage('checkout') {
         steps {
           git 'https://github.com/quamarar/json.git'
         }
        }
        stage('Adding Parameter')
         steps {
           script {
                    
                  env = build.getEnvironment(listener)
                  environment = env.get('environment')
                  filename = env.get('filename')


                   def builder = new JsonBuilder()
                   builder environment: environment, filename: filename
                   json = builder.toPrettyString()


                   println json
                   new File(build.workspace.toString() + "\\job.json").write(json)
           }
         }
       }
     }   
