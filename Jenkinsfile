pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage ("Clean up") {
            steps {
                deleteDir()
            }
        }
         stage ("Clone repo") {
             steps {
                 sh "git clone https://github.com/
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
            echo 'Pipeline exécuté avec succès !'
        }
        failure {
            echo 'Échec du pipeline. Vérifiez les logs.'
        }
    }
}
