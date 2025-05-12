pipeline {
    agent any  // Assurez-vous que Jenkins utilise un agent qui exécute Ubuntu

    stages {
        stage('Clean workspace') {
            steps {
                // Supprimer les fichiers dans le workspace
                sh 'rm -rf *'
            }
        }

        stage('Clone repository') {
            steps {
                // Cloner votre dépôt Git
                sh 'git clone https://github.com/Rihab123-ar/tp2jenkins.git'
            }
        }

        stage('Build and package') {
            steps {
                // Exécuter Maven pour la construction du projet
                dir('tp2jenkins/exp1-spring') {
                    sh 'mvn clean install'
                }
            }
        }

        stage('Build Docker image') {
            steps {
                // Construire l'image Docker
                dir('tp2jenkins/exp1-spring') {
                    sh 'docker build -t docexp1-spring .'
                }
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                // Lancer Docker Compose pour déployer
                dir('tp2jenkins/exp1-spring') {
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
