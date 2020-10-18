pipeline {
  environment {
    registry = "ishikasishodiya123/CRUD-App"
    registryCredential = 'ishikasishodiya123'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/ishikasishodiya/CRUD-App.git'
      }
    }
    stage('Build') {
       steps {
         sh 'docker build -t simple-web-application .'
       }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
         script {
            docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}