pipeline {
  agent {
    docker {
      image 'maven:latest'
    }
    
  }
  stages {
    stage('build') {
      steps {
        sh 'mvn generate'
      }
    }
    stage('Test Unitaire') {
      steps {
        parallel(
          "Test Unitaire": {
            sleep 5
            
          },
          "Test Fonctionnel": {
            sleep 10
            
          },
          "Test d'integration": {
            sleep 2
            
          }
        )
      }
    }
    stage('PROD ?') {
      steps {
        input(message: 'Voulez vous mettre en prod', id: 'prod', ok: 'Yeah')
      }
    }
    stage('MEP') {
      steps {
        echo 'On est en prod'
      }
    }
  }
}