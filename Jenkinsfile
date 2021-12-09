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

    stage('sonarqube-scanner') {
      def sonarqubeScannerHome = tool name: 'sonar', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
      withCredentials([string(credentialsId: 'sonar', variable: 'sonarLogin')]) {
        sh "${sonarqubeScannerHome}/bin/sonar-scanner -Dsonar.host.url=http://141.95.160.233:9000/ -Dsonar.login=${sonarLogin} -Dsonar.projectName=project2 -Dsonar.projectVersion=${env.BUILD_NUMBER} -Dsonar.projectKey=jnknsSnrqb2  -Dsonar.sources=./ -Dsonar.language=java -Dsonar.java.binaries=."
      }
    }


   stage('SonarQube analysis') {
	def scannerHome = tool 'sonar'
    	withSonarQubeEnv('sonar'){
      		sh "${scannerHome}/bin/sonar-scanner -Dsonar.host.url=http://141.95.160.233:9000/ -Dsonar.projectName=project2 -Dsonar.projectVersion=${env.BUILD_NUMBER} -Dsonar.projectKey=jnknsSnrqb2  -Dsonar.sources=./ -Dsonar.language=java -Dsonar.java.binaries=."
    	}
   }


   stage('Gate Quality'){
   	waitForQualityGate abortPipline : true
   }
}
