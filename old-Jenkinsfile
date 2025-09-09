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
           sh 'npm test || true'
      }
    }
    stage('Generate Coverage Report') {
      steps {
         echo "Generating coverage report ..."
           sh 'npm run coverage || true'
      }
    }
    stage('NPM Audit (Security Scan)') {
      steps {
         echo "Auditing..."
           sh 'npm audit || true'
      }
    }
  }
}
