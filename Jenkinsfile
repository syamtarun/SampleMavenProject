pipeline {
   agent any
   parameters {
     gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
   }
   stages{
       stage('git clone'){
           steps{
               git branch: "${params.Branch}", url: 'https://github.com/devops-surya/SampleMavenProject.git'
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
             'junit 'target/surefire-reports/*.xml'
           }
           
       }

   }
}
