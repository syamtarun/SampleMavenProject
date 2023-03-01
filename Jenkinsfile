pipeline {
  agent any
  triggers {
      upstream(upstreamProjects: 'SMP_PipelineJob', threshold: hudson.model.Result.SUCCESS)
  }
  stages {
    stage('Git clone') {
      steps {
        git credentialsId: '627d81ae-5ed6-471b-afc8-90c69fadd554', url: 'https://github.com/devops-surya/SampleMavenProject.git'
      }
    }
    stage('Build the code') {
        steps{
            sh 'mvn package'
        }
    }
    stage('Archive the artifacts') {
        steps{
            archive 'target/*.jar'
        }
    }
    stage('publish junit test reports') {
        steps{
            junit 'target/surefire-reports/*.xml'
        }
    }
  }
}
