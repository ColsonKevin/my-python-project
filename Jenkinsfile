pipeline {
    agent any 
    stages {
    	stage('flak8 et tests') {
		stage('flak8 installation') {
			steps {
				script {
					sh 'python3 --version'
					sh 'python3 -m flake8 --version'
				}
				
			}
		}
		stage ('pytest installation') {
			steps {
			}
		}
	}
    }
}

