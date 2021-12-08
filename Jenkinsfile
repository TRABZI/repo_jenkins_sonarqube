#!groovy
node {

    stage('Clone') {
        git 'https://github.com/TRABZI/homeWork_TP_Jenkins_webhook_sonar.git'
    }
   
    stage('SonarQube analysis') {
        def scannerHome= tool 'sonar-scanner'
        withSonarQubeEnv(credentialsId: 'sonarqubeToken', installationName: 'sonar') {
          sh '''$SCANNER_HOME/bin/sonar-scanner \
          -D sonar.login=admin \
          -D sonar.password=admin1 \
          -D sonar.projectBaseDir=/var/lib/jenkins/workspace/HomeWork1_TP_Jenkins \
         -Dsonar.projectKey=projectKey \
         -Dsonar.projectName=projectName \
         -Dsonar.sources=/  '''
       }
     }
   
   stage('SQuality Gate') {
	timeout(time: 1, unit: 'MINUTES') {
       	waitForQualityGate abortPipeline: true
       }
   }
}
