pipeline {
    agent any
	
    environment {
	IMAGE_NAME = "myapp"
	IMAGE_TAG = "latest"
}
    stages {
        
        stage('Build Docker Image') {
            steps {
                script {
                    //dockerImage = docker.build("pyapp:${env.BUILD_NUMBER}")
                    sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ." 
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    //dockerImage.run("-p 5000:5000")
		   			sh "docker rm -f demo-container || true"
                    sh "docker run -d -p 5000:5000 --name demo-container ${IMAGE_NAME}:${IMAGE_TAG}" 

                }
            }
        }
    }
}
