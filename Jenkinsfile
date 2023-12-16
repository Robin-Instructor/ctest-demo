pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Clean and compile the Java application
                    sh 'javac HelloChatGPT.java'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image
                    sh 'docker build -t hello-chatgpt .'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Run Docker container and map port 80
                    sh 'docker run -d -p 80:80 --name hello-chatgpt-container hello-chatgpt'
                }
            }
        }
    }

    post {
        always {
            // Cleanup: Remove the Docker container
            cleanup {
                sh 'docker rm -f hello-chatgpt-container || true'
            }
        }
    }
}
