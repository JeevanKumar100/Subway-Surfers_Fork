pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/JeevanKumar100/Subway-Surfers_Fork.git'  // replace with your repo URL
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("mygame:latest")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 8080:80 --name mygame-container mygame:latest'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline Finished'
        }
    }
}
