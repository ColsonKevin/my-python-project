pipeline {
    agent any 
    stages {
    	stage('flak8 et tests') {
		parallel {
			stage('installation flak8') {
				steps {
					sh 'python3 --version'
					sh 'python3 -m flake8 --version'
				}
			}
			stage('installation pytest') {
				steps {
					withPythonEnv('python3') {
						sh 'pip install pytest'
					}
				}
			}
		}
	}
    }
}

