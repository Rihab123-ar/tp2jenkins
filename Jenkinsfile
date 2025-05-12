pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages {
    stage('Clean workspace') {
      steps {
        deleteDir()
      }
    }
    
    stage('Clone repository') {
      steps {
        bat 'git clone https://github.com/Rihab123-ar/tp2jenkins.git'
      }
    }
    
    stage('Build and package') {
  steps {
    dir('tp2jenkins/exp1-spring') {
      bat 'mvn clean install'  // Exécuter Maven dans le répertoire où se trouve le pom.xml
    }
  }
}

    
    stage('Build Docker image') {
      steps {
        dir('tp2jenkins/exp1-spring') {
          bat 'docker build -t docexp1-spring .'
        }
      }
    }
    
    stage('Deploy with Docker Compose') {
      steps {
        dir('tp2jenkins/exp1-spring') {
          bat 'docker compose up -d'
        }
      }
    }
  }
}
