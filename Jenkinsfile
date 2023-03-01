pipeline {
  agent any
  stages {
    stage('Git clone') {
      steps {
        git branch: "${params.BRANCH}", url: 'https://github.com/devops-surya/SampleMavenProject.git'
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
