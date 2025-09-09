pipeline {
  agent any

  stages {
    stage('Notify Midway') {
      steps {
        echo 'Halfway there...'
      }
      post {
        always {
          emailext(
            to: 'brennanterreoz@gmail.com',
            subject: 'Midway Notification',
            body: 'The pipeline reached the Notify Midway stage.',
            attachLog: true,
            mimeType: 'text/plain'
          )
        }
      }
    }
  }
}

