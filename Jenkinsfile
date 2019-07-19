pipeline {
    agent {
    	label 'docker-mule'
    }
    stages {
      	stage('Checkout') {
            steps {
		checkout scm

            }
        }
        stage ('Build') {
            steps {
               
                echo 'Building application...'
              	archiveArtifacts(artifacts: '**/target/*.zip', onlyIfSuccessful: true, fingerprint: true)
            
        }
	}
      	stage('Deploy') {
            steps {
                echo 'Deploying application...'
              	bat 'mvn -Dmaven.repo.local="~/.m2/repository" package mule:deploy'
            }
        }
      
    }
}


