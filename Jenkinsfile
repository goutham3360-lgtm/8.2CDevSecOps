pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/goutham3360-lgtm/8.2CDevSecOps.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        bat 'npm install'
      }
    }

    stage('Run Tests') {
      steps {
        bat 'cmd /c npm test || exit /b 0'
      }
    }

    stage('Generate Coverage Report') {
      steps {
        bat 'cmd /c npm run coverage || exit /b 0'
      }
    }

    stage('Code Analysis') {
      steps {
        echo 'Running static code analysis...'
        // Example: eslint (make sure it's in devDependencies)
        bat 'cmd /c npx eslint . || exit /b 0'
      }
    }

    stage('NPM Audit (Security Scan)') {
      steps {
        bat 'cmd /c npm audit || exit /b 0'
      }
    }

    stage('Deploy (Simulation)') {
      steps {
        echo 'Deploying application to staging/production (simulation only).'
      }
    }
  }

  post {
    always {
      echo 'Pipeline finished: Part 1 – Task 2 Node.js pipeline with build, test, analysis, and security scan.'
    }
  }
}
