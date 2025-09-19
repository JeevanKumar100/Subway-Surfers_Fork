pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/JeevanKumar100/Subway-Surfers_Fork.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t subway-surfers:latest .'
            }
        }

        stage('Deploy Container') {
            steps {
                // Stop any existing container
                sh 'docker rm -f subway-surfers-container || true'
                // Start new container
                sh 'docker run -d -p 8080:80 --name subway-surfers-container subway-surfers:latest'
            }
        }
    }

    post {
        always {
            echo 'Done! 🚀'
        }
    }
}
