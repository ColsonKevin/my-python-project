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
					 sh 'python3 pip install flask'
					 sh 'python3 pip install pytest'
					 sh 'python3 pytest | tee report.txt'
				}
			}
		}
	}
    }
}

