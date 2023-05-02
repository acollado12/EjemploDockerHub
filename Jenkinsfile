pipeline {
    agent any
    environment{
        DOCKERHUB_CREDS = credentials('7516b481-9123-4470-905a-26031b2ff479')
    }
    stages {
        stage('Clone Repo') {
            steps {
                checkout scm
                sh 'ls *'
            }
        }
        stage('Build Image') {
            steps {
                //Aquí debes poner tu github
		sh 'docker build -t https://github.com/acollado12/EjemploDockerHub .'
            }
        }
        stage('DockerHUB Login') {
            steps {
                
                sh 'echo $DOCKERHUB_CREDS_PSW | docker login -u $DOCKERHUB_CREDS_USR --password-stdin'                
                }
            }
        stage('Docker Push') {
            steps {
		//Aquí debes poner tu github
                sh 'docker push https://github.com/acollado12/EjemploDockerHub'
                }
            }
        }
    post {
		always {
			sh 'docker logout'
		}
	 }
    }

