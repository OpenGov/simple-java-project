pipeline {
    agent {
        docker { image 'openjdk:11.0.9' }
    }
    stages {
        stage('SCM') {
            steps{
                checkout scm
            }
        }
        stage('SonarQube Analysis') {
            def scannerHome = tool 'SonarScanner';
            steps{
                withSonarQubeEnv() {
                  sh "mvn clean install"
                  sh "${scannerHome}/bin/sonar-scanner -X"  
                }     
            }
       }
    }
}
