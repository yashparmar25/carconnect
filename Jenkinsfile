pipeline {
    agent any

    environment {
        PROJECT_NAME = "carconnect"
        DOCKER_COMPOSE_FILE = "docker-compose.yml"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/yashparmar25/carconnect.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                script {
                    echo "🛠️ Building Docker images..."
                    sh 'docker-compose build'
                }
            }
        }

        stage('Run Containers') {
            steps {
                script {
                    echo "🚀 Starting containers..."
                    sh 'docker-compose down'
                    sh 'docker-compose up -d'
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                script {
                    sh 'docker ps'
                }
            }
        }
    }

    post {
        success {
            echo "✅ Deployment successful!"
        }
        failure {
            echo "❌ Build failed. Check the logs."
        }
    }
}
