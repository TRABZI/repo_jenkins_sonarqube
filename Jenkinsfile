node {

    stage('Clone') {
        	git 'https://github.com/TRABZI/homeWork_TP_Jenkins_webhook_sonar.git'
    }

    stage('Build') {
        	sh label: '', script: 'javac Main.java'
    }

    stage('Run') {
        	sh label: '', script: 'java Main'
    }

    stage('sonar-scanner') {
      def sonarqubeScannerHome = tool name: 'sonar', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
      withCredentials([string(credentialsId: 'sonar', variable: 'sonarLogin')]) {
        sh "${sonarqubeScannerHome}/bin/sonar-scanner -e -Dsonar.host.url=http://141.95.160.233:9000/ -Dsonar.login=${sonarLogin} -Dsonar.projectName=sq -Dsonar.projectVersion=${env.BUILD_NUMBER} -Dsonar.projectKey=GS -Dsonar.sources=./ -Dsonar.language=java -Dsonar.java.binaries=."
      }
    }
}
