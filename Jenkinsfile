pipeline {
  agent {
    docker {
      args '-p 3002:3000'
      image 'node:6-alpine'
    }

  }
  stages {
    stage('Install') {
      steps {
        sh 'npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
    stage('Approve') {
      when {
        branch 'production'
      }
      steps {
        input(message: '¿Se aprueba?', submitter: 'gabo')
      }
    }
    stage('Deploy to development') {
      when {
         branch 'development'
      }
      steps {
        echo 'Succesful'
      }
    }
    stage('Deploy to production') {
      when {
         branch 'production'
      }
      steps {
        echo 'Succesful'
      }
    }
  }
}
