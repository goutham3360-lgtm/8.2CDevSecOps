pipeline {
    agent any
    options { timestamps() }
    tools {
        maven 'M3'  // use the Maven installation you configured
    }
    triggers { pollSCM('H/5 * * * *') }

    stages {

        stage('Stage 1: Build') {
            steps {
                echo 'Compiling and packaging the code...'
                bat 'mvn clean package -DskipTests=true'
            }
        }

        stage('Stage 2: Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                bat 'mvn test'
            }
        }

        stage('Stage 3: Code Analysis') {
            steps {
                echo 'Static analysis to enforce coding standards.'
                echo 'Tool: SpotBugs / Checkstyle / PMD via Maven plugins.'
            }
        }

        stage('Stage 4: Security Scan') {
            steps {
                echo 'Scanning dependencies and source for vulnerabilities.'
                echo 'Tool: OWASP Dependency-Check or Snyk.'
            }
        }

        stage('Stage 5: Deploy to Staging') {
            steps {
                echo 'Deploying artifact to staging environment (simulation).'
            }
        }

        stage('Stage 6: Integration Tests on Staging') {
            steps {
                echo 'Running end-to-end tests in staging environment.'
            }
        }

        stage('Stage 7: Deploy to Production') {
            steps {
                echo 'Deploying artifact to production environment (simulation).'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished: Part 1 – Task 2 design with actual build & test integration.'
        }
    }
}
