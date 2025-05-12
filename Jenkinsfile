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
        bat 'mvn clean install'  // Plus besoin de dir() car pom.xml est à la racine
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
