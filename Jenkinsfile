pipeline {
    agent any

    environment {
        PROJECT_DIR = "exp1-spring"
        DOCKER_IMAGE = "docexp1-spring"
    }

    stages {
        stage('Build and package with Maven') {
            steps {
                echo '📦 Construction du projet avec Maven...'
                dir('tp2jenkins/exp1-spring') {
    sh 'mvn clean install'
}
            }
        }

        stage('Build Docker image') {
            steps {
                echo "🐳 Construction de l'image Docker..."
                dir("${env.PROJECT_DIR}") {
                    sh "docker build -t ${env.DOCKER_IMAGE} ."
                }
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                echo '🚀 Déploiement avec Docker Compose...'
                dir("${env.PROJECT_DIR}") {
                    sh 'docker-compose up -d'
                }
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline exécuté avec succès !'
        }
        failure {
            echo '❌ Échec du pipeline. Vérifiez les logs.'
        }
    }
}
