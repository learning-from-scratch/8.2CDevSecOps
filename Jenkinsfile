pipeline {
  agent any

  stages {
    stage('Notify Midway') {
      steps {
        echo 'Halfway there...'
      }
      post {
        success {
          emailext(
            to: 'brennanterreoz@gmail.com',
            subject: 'Smoke: SUCCESS',
            body: 'Success. Log attached.',
            attachLog: true,
            mimeType: 'text/plain'
          )
        }
        failure {
          emailext(
            to: 'brennanterreoz@gmail.com',
            subject: 'Smoke: FAILURE',
            body: 'Failure. Log attached.',
            attachLog: true,
            mimeType: 'text/plain'
          )
        }
      }
    }
  }
}

