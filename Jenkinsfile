pipeline {
    agent any

    environment {
        PROJECT_DIR = "tp2jenkins/exp1-spring"
        DOCKER_IMAGE = "docexp1-spring"
    }

    stages {
        stage('Clean workspace') {
            steps {
                echo '🧹 Nettoyage du workspace...'
                sh 'rm -rf *'
            }
        }

        stage('Clone repository') {
            steps {
                echo '🔄 Clonage du dépôt Git...'
                sh 'git clone https://github.com/Rihab123-ar/tp2jenkins.git'
            }
        }

        stage('Build and package with Maven') {
            steps {
                echo '📦 Construction du projet avec Maven...'
                dir("${env.PROJECT_DIR}") {
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
