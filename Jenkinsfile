node {
    
	stage('Clone') {
        	git 'https://github.com/TRABZI/homeWork_TP_Jenkins_webhook_sonar.git'
    	}
    
    	stage('scan'){
    		steps{
        		withSonarQubeEnv(installationName: 'sq1'){
                		sh './mvnw clean org.sonarsource.scanner.maven:sonar-maven-plug:3.9.0.2155:sonar'
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
