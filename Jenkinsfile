pipeline {
    agent any

    stages {
        // Stage 1: Build (Simulated)
        stage('Build') {
            steps {
                echo "Building code..."
            }
        }

        // Stage 2: Unit Tests (Simulated)
        stage('Unit Tests') {
            steps {
                echo "Running unit tests..."
            }
            post {
                always {
                    emailext (
                        subject: "Test Results - ${currentBuild.currentResult}",
                        body: "Unit tests completed! Status: ${currentBuild.currentResult}",
                        to: "akshitmittal1718@gmail.com", 
                        replyTo: "akshitmittal1718@gmail.com"
                    )
                }
            }
        }

        // Stage 3: Code Analysis (Simulated)
        stage('Code Analysis') {
            steps {
                echo "Checking code quality..."
            }
        }

        // Stage 4: Security Scan (Simulated)
        stage('Security Scan') {
            steps {
                echo "Scanning for vulnerabilities..."
            }
            post {
                always {
                    emailext (
                        subject: "Security Scan - ${currentBuild.currentResult}",
                        body: "Security scan completed! Status: ${currentBuild.currentResult}",
                        to: "akshitmittal1718@gmail.com" 
                    )
                }
            }
        }

        // Stage 5: Deploy to Staging (Simulated)
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to staging..."
            }
        }

        // Stage 6: Integration Tests (Simulated)
        stage('Integration Tests') {
            steps {
                echo "Running integration tests..."
            }
        }

        // Stage 7: Deploy to Production (Simulated)
        stage('Deploy to Production') {
            steps {
                echo "Deploying to production..."
            }
        }
    }
}
