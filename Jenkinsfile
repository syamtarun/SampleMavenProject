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
        sh "mvn sonar:sonar &
  -Dsonar.projectKey=SMP-Project &
  -Dsonar.host.url=http://18.181.192.127:9000 &
  -Dsonar.login=8d85500ed67cd9ccf0b996719acea35dc7ba183e"
    }
        }
        }
       
    }
}
