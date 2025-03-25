pipeline {
    agent any
    environment {
	DOCKER_LOGIN = 'kevincolson'
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
			withCredentials([string(credentialsId:'DOCKER_PASSWORD_KEVIN', variable:'DOCKER_PASS')]) {
				sh 'docker build -t kevincolson/my-python-app:latest .'
				sh 'docker login -u $DOCKER_LOGIN -p $DOCKER_PASS'
				sh 'docker push kevincolson/my-python-app:latest'
			}
		}
	}
    }
}

