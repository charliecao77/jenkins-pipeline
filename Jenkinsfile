pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        echo 'checkout'
      }
    }

    stage('sbx3') {
      steps {
        sh './deploy.sh SBX3 sbx3'
      }
    }

    stage('sbx4') {
      steps {
        sh './deploy.sh SBX4 sbx4'
      }
    }

    stage('nonprod') {
      steps {
        echo 'nonprod'
      }
    }

    stage('Prod') {
      steps {
        echo 'deploy on Production'
      }
    }

  }
}