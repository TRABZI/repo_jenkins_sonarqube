node {
    stage('Clone') {
        git 'https://github.com/TRABZI/homeWork_TP_Jenkins_webhook_sonar.git'
    }


    stage('Sonarqube') {
    	environment {
        	scannerHome = tool 'sonarqube'
    	}
    	steps {
        	withSonarQubeEnv('sonarqube') {
            		sh "${scannerHome}/bin/sonar-scanner"
        	}
        	timeout(time: 10, unit: 'MINUTES') {
            		waitForQualityGate abortPipeline: true
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
