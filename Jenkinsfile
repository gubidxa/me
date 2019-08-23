pipeline {
  agent any
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
        emailext(subject: 'Aprobar', body: 'Por favor aprueba', to: 'gabo', attachLog: true)
      }
    }
    stage('Approve') {
      steps {
        input(message: '¿Se aprueba?', submitter: 'gabo')
      }
    }
    stage('Deploy') {
      steps {
        echo 'Succesful'
      }
    }
  }
}