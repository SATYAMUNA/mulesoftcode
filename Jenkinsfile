pipeline {
  agent any
  stages {
      	stage('Checkout') {
            steps {
		checkout scm

            }
        }
    stage('Performance Test') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials') 
      }
      steps {
                echo 'Performance testing...'
              	bat 'mvn -Dmaven.repo.local="~/.m2/repository" verify'
              	archiveArtifacts(artifacts: '**/*.jtl', onlyIfSuccessful: true, fingerprint: true)
              	perfReport '**/*.jtl'
            }
    }
    
  }
}
