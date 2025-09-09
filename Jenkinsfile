pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        echo "Checkout repo..."
        git branch: 'main', url: 'https://github.com/learning-from-scratch/8.2CDevSecOps.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        echo "Installing dependencies ..."
        sh 'npm install'
      }
    }

    stage('Run Tests') {
      steps {
        echo "Running tests..."
        // let failures be failures so failure email can trigger
        sh 'npm test'
      }
      post {
         emailext(
         to: 'brennanterreoz@gmail.com',
         subject: 'Run Tests: SUCCESS',
         body: 'The Run Tests stage completed successfully.',
         attachLog: true
         )
      }
    }

    stage('Generate Coverage Report') {
      steps {
        echo "Generating coverage report ..."
        // if you want coverage not to fail the build, keep || true here
        sh 'npm run coverage || true'
      }
    }

    stage('NPM Audit (Security Scan)') {
      steps {
        echo "Auditing..."
        // let audit fail the stage so email triggers; remove || true
        sh 'npm audit'
      }
      post {
         emailext(
         to: 'brennanterreoz@gmail.com',
         subject: 'Security Scan: SUCCESS',
         body: 'The NPM Audit stage completed successfully.',
         attachLog: true
         )
      }
    }
  }
}

