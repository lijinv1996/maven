pipeline {
    agent any
    
    tools {
    maven 'localMaven'
  }
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        
        stage('Deliver for development') {
            when {
                branch 'devlop'
            }
       
            steps {
                build job: 'Deploy-to-staging'
            }
        }


    }
}
