pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
         echo "Checkout repo..."
         //   git branch: 'main', url: 'https://github.com/learning-from-scratch/8.2CDevSecOps.git'
      }
    }
    stage('Install Dependencies') {
      steps {
         echo "Installing dependencies ..."
         //   sh 'npm install'
      }
    }
    stage('Run Tests') {
      steps {
         echo "Running tests..."
         //   sh 'npm test || true'
      }
      post {
        success {
          emailext(
            to: "brennanterreoz@gmail.com",
            subject: "Run Tests: SUCCESS",
            body: "The Run Tests stage completed successfully.",
            attachLog: true
          )
        }
        failure {
          emailext(
            to: "brennanterreoz@gmail.com",
            subject: "Run Tests: FAILURE",
            body: "The Run Tests stage failed. Please see the attached log.",
            attachLog: true
          )
        }
      }
    }
    stage('Generate Coverage Report') {
      steps {
         echo "Generating coverage report ..."
         //   sh 'npm run coverage || true'
      }
    }
    stage('NPM Audit (Security Scan)') {
      steps {
         echo "Auditing..."
         //   sh 'npm audit || true'
      }
      post {
        success {
          emailext(
            to: "brennanterreoz@gmail.com",
            subject: "Security Scan: SUCCESS",
            body: "The NPM Audit stage completed successfully.",
            attachLog: true
          )
        }
        failure {
          emailext(
            to: "brennanterreoz@gmail.com",
            subject: "Security Scan: FAILURE",
            body: "The NPM Audit stage failed. Please see the attached log.",
            attachLog: true
          )
        }
      }
    }
  }
}
