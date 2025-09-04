pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/VincentDao25/8.2CDevSecOp.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test || true'  // allow continuation even if tests fail
            }
        }

        stage('Generate Coverage Report') {
            steps {
                sh 'npm run coverage || true'
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                sh 'npm audit || true'  // shows CVEs in output
            }
        }
    }
}
