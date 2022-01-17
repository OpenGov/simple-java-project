node {
  
  def containers = [
  OGContainer('jdk', 'openjdk', '11.0.9', [
    environmentVariables: [JAVA_OPTS: '-XshowSettings:vm'],
    resourceLimitCpu: '250m',
    resourceLimitMemory: '0.5Gi']
  )
  
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    container('jdk') {
    def scannerHome = tool 'SonarScanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner -X"
    }
   }
  }
}
