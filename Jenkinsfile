pipeline {
    agent any

    stages {
        // Stage 1: Build with Maven (Simulated)
        stage('Build') {
            steps {
                echo "[TOOL] Apache Maven: Compiling and packaging code"
                bat '''
                    echo mvn clean install > build.log
                    echo BUILD SUCCESS >> build.log
                '''
            }
        }

        // Stage 2: Unit Tests with JUnit (Simulated)
        stage('Unit Tests') {
            steps {
                echo "[TOOL] JUnit: Running unit tests"
                bat '''
                    echo JUnit Test Results > test-results.txt
                    echo ========================= >> test-results.txt
                    echo Tests Run: 20 >> test-results.txt
                    echo Passed: 20 >> test-results.txt
                    echo Failed: 0 >> test-results.txt
                '''
            }
            post {
                always {
                    emailext (
                        subject: "Unit Test Results - ${currentBuild.currentResult}",
                        body: "JUnit tests completed!\nStatus: ${currentBuild.currentResult}",
                        to: "akshit4759.be23@chitkara.edu.in",
                        replyTo: "akshit4759.be23@chitkara.edu.in",
                        attachmentsPattern: 'test-results.txt'
                    )
                }
            }
        }

        // Stage 3: Code Analysis with SonarQube (Simulated)
        stage('Code Analysis') {
            steps {
                echo "[TOOL] SonarQube: Checking code quality"
                bat '''
                    echo ^<html^>^<body^>^<h1^>SonarQube Report^</h1^>^<p^>Bugs: 0^</p^>^<p^>Code Smells: 3^</p^>^</body^>^</html^> > sonarqube-report.html
                '''
            }
        }

        // Stage 4: Security Scan with OWASP (Simulated)
        stage('Security Scan') {
            steps {
                echo "[TOOL] OWASP Dependency-Check: Scanning vulnerabilities"
                bat '''
                    echo ^<html^>^<body^>^<h1^>Security Report^</h1^>^<p^>Critical: 0^</p^>^<p^>High: 2^</p^>^</body^>^</html^> > security-scan.html
                '''
            }
            post {
                always {
                    emailext (
                        subject: "Security Scan Results - ${currentBuild.currentResult}",
                        body: "OWASP scan completed!\nStatus: ${currentBuild.currentResult}",
                        to: "akshit4759.be23@chitkara.edu.in",
                        attachmentsPattern: 'security-scan.html'
                    )
                }
            }
        }

        // Stage 5: Deploy to Staging with SCP (Simulated)
        stage('Deploy to Staging') {
            steps {
                echo "[TOOL] SCP/SSH: Deploying to staging server"
                bat '''
                    echo [INFO] Deploying app.war to staging > deploy-staging.log
                    echo [SUCCESS] Deployment completed >> deploy-staging.log
                '''
            }
        }

        // Stage 6: Integration Tests with Postman (Simulated)
        stage('Integration Tests') {
            steps {
                echo "[TOOL] Postman/Newman: Testing APIs"
                bat '''
                    echo {"run":{"stats":{"requests":{"total":10,"failed":0}},"failures":[]}} > postman-results.json
                '''
            }
        }

        // Stage 7: Deploy to Production with Docker (Simulated)
        stage('Deploy to Production') {
            steps {
                echo "[TOOL] Docker: Containerizing application"
                bat '''
                    echo docker build -t my-app:prod > docker-deploy.log
                    echo docker push my-app:prod >> docker-deploy.log
                '''
            }
        }
    }

    // Final email with all artifacts
    post {
        always {
            emailext (
                subject: "Pipeline Status: ${currentBuild.currentResult}",
                body: "Full pipeline completed!\nDetails: ${env.BUILD_URL}",
                to: "akshit4759.be23@chitkara.edu.in",
                attachmentsPattern: 'build.log,test-results.txt,sonarqube-report.html,security-scan.html,deploy-staging.log,postman-results.json,docker-deploy.log'
            )
        }
    }
}
