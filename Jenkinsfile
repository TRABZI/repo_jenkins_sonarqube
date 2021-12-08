node {
    stage('Clone') {
        git 'https://github.com/TRABZI/homeWork_TP_Jenkins_webhook_sonar.git'
    }
    stage('SonarQube analysis') {
        withSonarQubeEnv('SonarQube') {
                sh "./gradlew sonarqube"
        }
    }
    stage("Quality gate") {
        waitForQualityGate abortPipeline: true
    }
    stage('Build') {
        sh label: '', script: 'javac Main.java'
    }
    stage('Run') {
        sh label: '', script: 'java Main'
    }
}
