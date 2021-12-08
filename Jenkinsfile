#!groovy
pipeline {
agent any
environment {
   GIT_COMMIT_SHORT = sh(
     script: "printf \$(git rev-parse --short ${GIT_COMMIT})",
     returnStdout: true
    )
}
stages {
   stage('SonarQube analysis') {
    steps{
     environment {
       SCANNER_HOME = tool 'sonar-scanner'
     }

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
   }

  stage('SQuality Gate') {
     steps {
       timeout(time: 1, unit: 'MINUTES') {
       	waitForQualityGate abortPipeline: true
       }
    }
 }
}
}

