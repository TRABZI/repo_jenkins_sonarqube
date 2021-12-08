node {
    
	stage('Clone') {
        	git 'https://github.com/TRABZI/homeWork_TP_Jenkins_webhook_sonar.git'
    	}
    
    	stage('scan'){
    		steps{
        		withSonarQubeEnv(installationName: 'sq1'){
                		sh './mvnw clean sonar:sonar'
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
