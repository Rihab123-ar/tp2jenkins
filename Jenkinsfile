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
        bat "git clone https://github.com/Rihab123-ar/tp2jenkins.git"
      }
    }
    stage ("Generate backend image") {
      steps {
        dir("exp1-spring") {
          bat "mvn clean install"
          bat "docker build -t docexp1-spring ."
        }
      }
    }
    stage ("Run docker compose") {
      steps {
        dir("exp1-spring") {
          bat "docker compose up -d"
        }
      }
    }
  }
}
