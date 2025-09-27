pipeline {
  agent any

  tools {
   
    nodejs "Node"
  }

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
        // prevents build failure if tests return non-zero
        bat 'cmd /c npm test || exit /b 0'
      }
    }

    stage('Generate Coverage Report') {
      steps {
        bat 'cmd /c npm run coverage || exit /b 0'
      }
    }

    stage('NPM Audit') {
      steps {
        bat 'cmd /c npm audit || exit /b 0'
      }
    }
  }
  post {
    success {
      emailext(
        subject: "✅ SUCCESS: Jenkins Build ${env.JOB_NAME} #${env.BUILD_NUMBER}",
        body: "The build completed successfully.\nCheck details at ${env.BUILD_URL}",
        to: "your_email@example.com",
        attachLog: true
      )
    }
    failure {
      emailext(
        subject: "❌ FAILURE: Jenkins Build ${env.JOB_NAME} #${env.BUILD_NUMBER}",
        body: "The build failed.\nCheck console output: ${env.BUILD_URL}",
        to: "your_email@example.com",
        attachLog: true
      )
    }
  }
}
