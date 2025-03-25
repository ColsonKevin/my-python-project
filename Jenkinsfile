pipeline {
    agent any 
    stages {
    	stage('flak8 et tests') {
		parallel {
			stage('flak8') {
				steps {
					sh 'python3 --version'
					sh 'python3 -m flake8 --version'
					sh 'python3 -m flake8 . --count --show-source --statistics || true'
				}
			}
			stage('tests') {
				steps {
					 withPythonEnv('python3.11.2') {
					 	sh 'pip install -U pytest'
					 	sh 'pytest | tee report.txt'
					 }
				}
			}
		}
	}
    }
}

