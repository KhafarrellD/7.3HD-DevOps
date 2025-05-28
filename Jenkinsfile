pipeline {
    agent any

    environment {
        LOG_DIR = "logs"
    }

    stages {

        stage('Build') {
            steps {
                echo '🔧 Building the application...'
                sh 'mkdir -p build && echo "Compiled Python App" > build/app.txt'
                archiveArtifacts artifacts: 'build/app.txt'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running unit tests...'
                writeFile file: 'test-results.txt', text: 'All unit tests passed.'
                archiveArtifacts artifacts: 'test-results.txt'
            }
        }

        stage('Code Quality') {
            steps {
                echo '🔍 Running code quality check...'
                writeFile file: 'code-quality-report.txt', text: 'No code smells. Readable and maintainable.'
                archiveArtifacts artifacts: 'code-quality-report.txt'
            }
        }

        stage('Security') {
            steps {
                echo '🔒 Performing security scan...'
                writeFile file: 'security-scan.txt', text: 'No vulnerabilities found.'
                archiveArtifacts artifacts: 'security-scan.txt'
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying to test environment...'
                sh 'mkdir -p deploy && cp build/app.txt deploy/app.txt'
                archiveArtifacts artifacts: 'deploy/app.txt'
            }
        }

        stage('Release') {
            steps {
                echo '🎉 Releasing to production...'
                sh 'mkdir -p production && cp deploy/app.txt production/app.txt'
                archiveArtifacts artifacts: 'production/app.txt'
            }
        }

        stage('Monitoring') {
            steps {
                echo '📈 Monitoring application health...'
                writeFile file: 'monitoring-log.txt', text: 'All systems operational. No alerts.'
                archiveArtifacts artifacts: 'monitoring-log.txt'
            }
        }
    }

    post {
        always {
            echo '✅ Pipeline execution complete.'
        }
    }
}
