pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages {
    stage('Clean workspace') {
      steps {
        sh 'rm -rf *'  // Supprime tous les fichiers et dossiers dans le répertoire de travail
      }
    }
    
    stage('Clone repository') {
      steps {
        sh 'git clone https://github.com/Rihab123-ar/tp2jenkins.git'
      }
    }
    
    stage('Check POM existence') {
      steps {
        sh 'ls tp2jenkins/exp1-spring/pom.xml'  // Vérifie si le pom.xml existe
      }
    }
    
    stage('Build and package') {
      steps {
        dir('tp2jenkins/exp1-spring') {
          sh 'mvn clean install'  // Exécuter Maven dans le répertoire contenant le pom.xml
        }
      }
    }
    
    stage('Build Docker image') {
      steps {
        dir('tp2jenkins/exp1-spring') {
          sh 'docker build -t docexp1-spring .'
        }
      }
    }
    
    stage('Deploy with Docker Compose') {
      steps {
        dir('tp2jenkins/exp1-spring') {
          sh 'docker-compose up -d'
        }
      }
    }
  }
}
