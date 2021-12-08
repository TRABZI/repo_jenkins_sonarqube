node {
    stage('Clone') {
        git 'https://github.com/TRABZI/homeWork_TP_Jenkins_webhook_sonar.git'
    }

    
    stage ('Scan and Build Jar File') {
    	steps {
        	withSonarQubeEnv(installationName: 'sonarqube_server', credentialsId: 'sqt') {
                	sh 'mvn clean package sonar:sonar'
                }
            }
        }

    stage('Build') {
        sh label: '', script: 'javac Main.java'
        }

    stage('Run') {
        sh label: '', script: 'java Main'
        }
}
