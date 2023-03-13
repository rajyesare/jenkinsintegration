pipeline {
    agent any
    
    stages {
        stage('Remove Docker Container and Image') {
            steps {
                sh 'docker stop 7c2cc42f7a54'
                sh 'docker rm 7c2cc42f7a54'
                sh 'docker rmi 74b7e83b1921'
		sh 'docker rmi e1635ddc0b1d'
            }
	}
	
        stage('Build Docker Image') {
            steps {
                script {
                    def dockerfile = 'Dockerfile'
                    docker.build('my-image-name:latest', "-f ${dockerfile} .")
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    docker.image('my-image-name:latest').run('-p 80:80')
                }
            }
        }
    }
}
