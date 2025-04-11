pipeline {
    agent any // Run on any available agent

    stages {
        stage('Checkout') {
            steps {
                git branch: '${BRANCH_NAME}', credentialsId: '958d9274-b20d-4187-bfcc-9bcc112956b7', url: 'https://github.com/nkhk98/Devopsbits-repo.git'
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Building the application..."'
                sh './main.sh' // Execute our sample script
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
                sh 'echo "No tests defined in this example"'
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
