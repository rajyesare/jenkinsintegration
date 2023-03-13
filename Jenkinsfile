pipeline {
    agent any
    
    stages {
       /*
	 stage('Remove Docker Container and Image') {
            steps {
                sh 'docker stop 488a1a3c0590'
                sh 'docker rm 488a1a3c0590'
                sh 'docker rmi my-image-name'
		sh 'docker rmi debian'
            }
	}
	*/
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
