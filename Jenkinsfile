pipeline {
    agent any

    environment {
        IMAGE_NAME = 'gaming'
        CONTAINER_NAME = 'city-app'
        PORT = '8080'
    }

    stages {
        stage('Deploy Prebuilt Docker Image') {
            steps {
                script {
                    // Stop and remove existing container if running
                    sh "docker rm -f ${CONTAINER_NAME} || true"

                    // Run the prebuilt image
                    sh "docker run -d -p ${PORT}:80 --name ${CONTAINER_NAME} ${IMAGE_NAME}"
                }
            }
        }
    }

    post {
        success {
            echo "🎮 Deployed 3D City Game at http://<your-server-ip>:${PORT}"
        }
        failure {
            echo '💥 Deployment failed!'
        }
    }
}

