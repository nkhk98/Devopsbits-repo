pipeline {
    agent any // Run on any available agent

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: '958d9274-b20d-4187-bfcc-9bcc112956b7', url: 'https://github.com/nkhk98/Devopsbits-repo.git'
            }
        }
        stage('Build') {
            agent any
            steps {
                sh 'echo "Building the application..."'
                sh 'echo "Simulating successful build"' // Simulate a successful build
                // In a real scenario, replace the 'echo' with your actual build commands
            }
        }
        stage('Test') {
            agent any
            steps {
                sh 'echo "Running tests..."'
                sh 'echo "No tests defined in this example"'
                sh 'echo "Simulating successful tests"' // Simulate successful tests
                // In a real scenario, replace the 'echo' with your actual test commands
            }
        }
        stage('Deploy to Staging') {
            agent { label 'local-agent' } // Run on the specific agent
            steps {
                sh 'echo "Deploying to Staging environment..."'
                sh 'mkdir -p /tmp/staging'
                sh 'cp main.sh /tmp/staging/'
                sh 'echo "Application deployed to /tmp/staging"'
            }
        }
        stage('Deploy to Production') {
            agent any
            steps {
                input message: 'Approve deployment to Production?', ok: 'Deploy!'
                sh 'echo "Deploying to Production environment..."'
                sh 'mkdir -p /tmp/production'
                sh 'cp main.sh /tmp/production/'
                sh 'echo "Application deployed to /tmp/production"'
            }
        }
    }
    post {
        success {
            echo 'Pipeline finished successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
        always {
            echo 'Cleaning up...'
        }
    }
}
