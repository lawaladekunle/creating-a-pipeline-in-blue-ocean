pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh '''

npm install'''
          }
        }

        stage('Int-Build') {
          steps {
            sh 'echo "Intermediate Build"'
          }
        }

      }
    }

    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }

  }
  environment {
    deck = 'dockerd'
  }
}