pipeline {
   agent any
   stages{
       stage('git clone'){
           steps{
               git credentialsId: '627d81ae-5ed6-471b-afc8-90c69fadd554', url: 'https://github.com/devops-surya/SampleMavenProject.git'
           }        
       }
       stage('build the code'){
           steps{
              sh 'mvn package'
           }
       }
       stage('archive the artifacts'){
           steps{
              archive 'target/*.jar'
           }          
       }
       stage('publish the junit reports'){
           steps{
              junit 'target/surefire-reports/*.xml'
           }
           
       }
       stage('rt server'){
           steps{
               rtServer (
                   id: 'Jfrog-OSS',
                   url: 'http://18.117.92.212:8082/artifactory',
                   username: 'admin',
                   password: 'Jfrog@123',
                   bypassProxy: true,
                   timeout: 300
               )

           }
       }
       stage('rt upload'){
           steps{
               rtUpload (
                   serverId: 'Jfrog-OSS',
                   spec: '''{
                         "files": [
                             {
                                 "pattern": "target/*.jar",
                                 "target": "Test/"

                             }
                                  ]
                   }''',
                        
               )

           }

       }

      }


    }
