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
        // Le pom.xml est à la racine du projet cloné
        dir('tp2jenkins') {
          bat 'mvn clean install'
        }
      }
    }
    
    stage('Build Docker image') {
      steps {
        dir('tp2jenkins') {
          bat 'docker build -t docexp1-spring .'
        }
      }
    }
    
    stage('Deploy with Docker Compose') {
      steps {
        dir('tp2jenkins') {
          bat 'docker compose up -d'
        }
      }
    }
  }
}
