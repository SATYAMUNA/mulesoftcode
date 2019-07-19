pipeline {
  agent any
  stages {
      	stage('Checkout') {
            steps {
		checkout scm

            }
        }
    stage('Deploy ARM') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials') 
      }
      steps {
        //bat 'mvn deploy -P arm -Darm.target.name=proxy-cluster -Danypoint.username=MULEDOCKER  -Danypoint.password=MYnoki@523@' 
	      bat 'mvn -Dmaven.repo.local="~/.m2/repository" package mule:deploy'
      }
    }
    
  }
}
