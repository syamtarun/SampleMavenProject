pipeline{
    agent any
    stages{
       stage('GetCode'){
            steps{
                git credentialsId: '627d81ae-5ed6-471b-afc8-90c69fadd554', url: 'https://github.com/devops-surya/SampleMavenProject.git'
            }
         }        
       stage('Build'){
            steps{
                sh 'mvn clean package'
            }
         }
        stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        withSonarQubeEnv('sonarqube-8.9.2') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
        sh "mvn sonar:sonar \
  -Dsonar.projectKey=SMP-Project \
  -Dsonar.host.url=http://18.220.243.206:9000 \
  -Dsonar.login=dd65a550f76902a84b17b220615fc0e9b847f844"
    }
        }
        }
       
    }
}
