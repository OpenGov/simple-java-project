pipeline {
    agent {
      label 'docker'
    }
    stages {
        stage('SCM') {
          agent {
              docker {
                label 'docker'
                image 'openjdk:11.0.9'
              }
          }   
          steps {
            checkout scm
          }
        }
        stage('SonarQube Analysis') {
          environment {
              scannerHome = tool 'SonarScanner'
            }  
          agent {
            docker {
              label 'docker'
                image 'openjdk:11.0.9'
            }
          } 
          steps{
            withSonarQubeEnv() {
                sh "mvn clean install"
                sh "${scannerHome}/bin/sonar-scanner -X"  
            }     
          }
       }
    }
}
