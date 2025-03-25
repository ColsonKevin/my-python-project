pipeline {
    agent any
    environment {
	DOCKER_LOGIN=kevincolson
	DOCKER_PASS=dckr_pat_R99-W6LixPZy2AB8v0upvtf6TTI
    }  
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
					 //sh 'python3 pip install flask'
					 //sh 'python3 pip install pytest'
					 sh 'python3 pytest | tee report.txt'
				}
			}
		}
	}
	stage('docker') {
		steps {
			sh 'docker build -t kcolson/my-python-app:latest .'
			sh 'docker login -u $DOCKER_LOGIN -p $DOCKER_PASS'
			sh 'docker push kcolson/my-python-app:latest'
		}
	}
    }
}

