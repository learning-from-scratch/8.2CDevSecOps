pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/learning-from-scratch/8.2CDevSecOps.git'
      }
    }
    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }
    stage('Run Tests') {
      steps {
        sh 'npm test || true'
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
        sh 'npm run coverage || true'
      }
    }
    stage('NPM Audit (Security Scan)') {
      steps {
        sh 'npm audit || true'
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
