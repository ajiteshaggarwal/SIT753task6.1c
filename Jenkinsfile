pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building the project...'
                // Example: sh 'mvn clean packkkkage'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Example: sh 'mvn test'
            }
            post {
                always {
                    // Send email after the Unit and Integration Tests stage
                    emailext(
                        subject: "Jenkins Pipeline: Unit and Integration Tests - ${currentBuild.currentResult}",
                        body: """The Unit and Integration Tests stage has ${currentBuild.currentResult}.
                                 Please review the attached logs for details.""",
                        to: 'ajiteshaggarwal027@gmail.com',
                        attachLog: true
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Running the code analysis...'
                // Example: sh 'sonar-scanner'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Example: sh 'dependency-check.sh --project myProject --scan .'
            }
            post {
                always {
                    // Send email after the Security Scan stage
                    emailext(
                        subject: "Jenkins Pipeline: Security Scan - ${currentBuild.currentResult}",
                        body: """The Security Scan stage has ${currentBuild.currentResult}.
                                 Please review the attached logs for details.""",
                        to: 'ajiteshaggarwal027@gmail.com',
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
                // Example: sh 'scp target/*.jar user@staging-server:/path/to/deploy'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Example: sh 'curl -X GET http://staging-server/test-endpoint'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                // Example: sh 'scp target/*.jar user@production-server:/path/to/deploy'
            }
        }
    }
}